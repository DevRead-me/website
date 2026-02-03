# Tech Stack

Complete overview of technologies powering DevRead.me.

## Frontend Technologies

### React 18.2

**Version:** 18.2.x

**Purpose:** UI Component Framework

**Key Features Used:**

- Functional components with hooks
- useState for state management
- useEffect for side effects
- Concurrent rendering

**Why React:**

- Component reusability
- Virtual DOM efficiency
- Large ecosystem
- Developer experience

### Next.js 14

**Version:** 14.x

**Purpose:** React Framework & Build Tool

**Features:**

- App Router for routing
- API Routes for serverless functions
- Image optimization
- Automatic code splitting
- Built-in CSS support

**Architecture:**

- Server-side rendering (SSR) ready
- Static generation capable
- Incremental Static Regeneration (ISR)
- Dynamic routing support

### TypeScript 5.3

**Version:** 5.3.x

**Purpose:** Type Safety & Development Quality

**Usage:**

- Type definitions for all components
- Interface definitions for data structures
- Type checking at build time
- Better IDE support

**Benefits:**

- Catch errors early
- Improved code documentation
- Refactoring safety
- Developer productivity

## Styling & UI

### Tailwind CSS 3.3

**Version:** 3.3.x

**Purpose:** Utility-First CSS Framework

**Usage:**

- Responsive design classes
- Dark mode support
- Custom color schemes
- Component styling

**Classes Used:**

- Flexbox and Grid layouts
- Spacing and sizing
- Colors and typography
- Shadows and effects
- Hover and focus states

**Configuration:**

```javascript
// tailwind.config.js
module.exports = {
  theme: {
    extend: {
      colors: {
        // Custom colors
      },
    },
  },
};
```

### PostCSS 8.4

**Version:** 8.4.x

**Purpose:** CSS Processing & Transformation

**Plugins:**

- Tailwind CSS plugin
- Autoprefixer for vendor prefixes
- CSSNano for minification

### Framer Motion 12.30

**Version:** 12.30.x

**Purpose:** Advanced Animation Library

**Animations Used:**

- Page transitions
- Component entrance animations
- Interactive feedback animations
- Progress indicators
- Background effects

**Features:**

- Keyframes animations
- Gesture animations
- Drag support
- Orchestrated animations

**Example:**

```typescript
import { motion } from "framer-motion";

export function AnimatedCard() {
  return (
    <motion.div
      initial={{ opacity: 0, y: 20 }}
      animate={{ opacity: 1, y: 0 }}
      transition={{ duration: 0.5 }}
    >
      Content
    </motion.div>
  );
}
```

### Lucide React 0.563

**Version:** 0.563.x

**Purpose:** Icon Library

**Icons Used:**

- UI controls (buttons, arrows)
- Status indicators
- Feature icons
- Navigation elements

**Features:**

- SVG-based icons
- Customizable size/color
- Consistent design language
- Extensive icon set

**Usage:**

```typescript
import { ArrowRight, Zap, Download } from "lucide-react";

<ArrowRight size={24} />
```

## Backend & API

### Node.js

**Purpose:** JavaScript Runtime

**Used For:**

- Server-side code execution
- API processing
- File operations
- External API calls

### Next.js API Routes

**Path:** `app/api/generate/route.ts`

**Method:** POST

**Purpose:** Serverless function for documentation generation

**Request Handling:**

```typescript
export async function POST(request: Request) {
  // Parse request body
  const { content, options } = await request.json();

  // Validate input
  // Call services
  // Return response
}
```

**Features:**

- Automatic request parsing
- Error handling
- CORS support
- Streaming responses

## AI & Language Model

### Groq Cloud API

**Service:** Groq Inference Platform

**Model:** Llama 3.3 70B Versatile

**Specifications:**

- 70 billion parameters
- Context window: 8,192 tokens
- Training data: Up to April 2024
- Quantization: Mixed precision

**API Version:** OpenAI-compatible v1

**Endpoint:** `https://api.groq.com/openai/v1`

**Authentication:**

- API Key required
- Environment variable: `GROQ_API_KEY`
- Bearer token in headers

**Capabilities:**

- Text generation
- Code generation
- Summarization
- Question answering
- Content transformation

### Groq SDK

**Package:** `groq-sdk` v0.37.x

**Installation:**

```bash
npm install groq-sdk
```

**Usage:**

```typescript
import Groq from "groq-sdk";

const groq = new Groq({
  apiKey: process.env.GROQ_API_KEY,
});

const message = await groq.chat.completions.create({
  model: "llama-3.3-70b-versatile",
  messages: [
    { role: "system", content: "..." },
    { role: "user", content: "..." },
  ],
  stream: true,
});
```

**Features:**

- OpenAI SDK compatibility
- Streaming support
- Error handling
- Token counting

## File Management

### JSZip 3.10

**Purpose:** ZIP File Creation & Manipulation

**Version:** 3.10.x

**Usage:**

```typescript
import JSZip from "jszip";

const zip = new JSZip();
zip.file("README.md", content);
zip.folder("css").file("style.css", styleContent);

const blob = await zip.generateAsync({ type: "blob" });
```

**Features:**

- Create ZIP files in-memory
- Add files and folders
- Compression support
- Binary file handling

### File System (Node.js)

**Module:** `fs` (built-in)

**Usage:**

- Writing generated files
- Reading templates
- File validation

**Methods:**

- `fs.writeFile()` - Write content
- `fs.readFile()` - Read files
- `fs.mkdir()` - Create directories
- `fs.exists()` - Check file existence

## Environment & Configuration

### dotenv

**Purpose:** Environment Variable Management

**Usage:**

```javascript
// .env.local
GROQ_API_KEY=your_key_here
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

**Features:**

- Load variables from .env files
- Override with system variables
- Public variables prefix (NEXT*PUBLIC*)
- Development/production configs

## Development Tools

### ESLint

**Version:** Latest

**Purpose:** Code Quality & Style

**Config:**

```javascript
// .eslintrc.json
{
  "extends": ["next/core-web-vitals"],
  "rules": {
    // Custom rules
  }
}
```

**Checks:**

- Syntax errors
- Best practices
- Style consistency
- Security issues

### TypeScript Compiler

**Version:** 5.3.x

**Purpose:** Type Checking & Compilation

**Configuration:**

```json
{
  "compilerOptions": {
    "target": "ES2020",
    "lib": ["ES2020", "DOM"],
    "jsx": "react-jsx",
    "strict": true,
    "module": "ESNext",
    "moduleResolution": "bundler"
  }
}
```

### Prettier (Optional)

**Purpose:** Code Formatting

**Configuration:**

```javascript
module.exports = {
  semi: true,
  singleQuote: true,
  tabWidth: 2,
  trailingComma: "es5",
};
```

## Build & Deployment

### Next.js Build System

**Commands:**

```bash
npm run dev      # Development server
npm run build    # Production build
npm run start    # Production server
npm run lint     # Lint code
```

**Build Output:**

- Optimized JavaScript bundles
- CSS modules
- Image optimization
- Static HTML files

### Vercel (Optional Hosting)

**Features:**

- Zero-config deployment
- Automatic CI/CD
- Preview deployments
- Environment variables
- Serverless functions

### Docker Support

**Dockerfile Example:**

```dockerfile
FROM node:18-alpine

WORKDIR /app

COPY package*.json ./
RUN npm ci

COPY . .

ENV GROQ_API_KEY=${GROQ_API_KEY}

RUN npm run build

EXPOSE 3000

CMD ["npm", "run", "start"]
```

## Dependencies Summary

### Production Dependencies

```json
{
  "react": "18.2.x",
  "react-dom": "18.2.x",
  "next": "14.x",
  "groq-sdk": "0.37.x",
  "jszip": "3.10.x",
  "framer-motion": "12.30.x",
  "lucide-react": "0.563.x"
}
```

### Dev Dependencies

```json
{
  "@types/node": "20.x",
  "@types/react": "18.x",
  "typescript": "5.3.x",
  "tailwindcss": "3.3.x",
  "postcss": "8.4.x",
  "eslint": "latest",
  "eslint-config-next": "14.x"
}
```

## Performance Metrics

### Bundle Size

- **Initial Page Load:** ~150 KB
- **Main JS Bundle:** ~100 KB
- **CSS Bundle:** ~50 KB

### API Performance

- **Average Generation Time:** 25-35 seconds
- **API Response Time:** 20-30 seconds
- **ZIP Creation:** 1-2 seconds

### Infrastructure

- **Memory Usage:** ~200-300 MB
- **CPU Usage:** Minimal (event-driven)
- **Concurrent Requests:** Scalable

## Version Compatibility

| Technology | Version | Status |
| ---------- | ------- | ------ |
| Node.js    | 18+     | Stable |
| React      | 18.2.x  | Stable |
| Next.js    | 14.x    | Stable |
| TypeScript | 5.3.x   | Stable |
| Tailwind   | 3.3.x   | Stable |
| Groq SDK   | 0.37.x  | Stable |

## Technology Justification

### Why Next.js?

- Built on React (familiar)
- Built-in API routes (no separate backend)
- Excellent performance (image optimization)
- SSR/SSG capabilities
- Great DX

### Why TypeScript?

- Type safety catches errors early
- Better IDE support
- Self-documenting code
- Refactoring confidence
- Enterprise-grade quality

### Why Tailwind?

- Rapid development
- Small bundle size
- Highly customizable
- Responsive design built-in
- Excellent documentation

### Why Groq?

- State-of-the-art models
- Excellent inference speed
- Cost-effective
- OpenAI API compatibility
- Streaming support

### Why React + Framer Motion?

- Smooth, professional animations
- Better user experience
- Modern interaction patterns
- Easy to implement complex animations

## System Requirements

### Development

- Node.js 18 or higher
- npm/yarn package manager
- 2+ GB RAM
- 500MB disk space
- Modern code editor (VS Code recommended)

### Deployment

- Node.js 18+ runtime
- Environment for API key storage
- HTTPS support
- 50MB disk space minimum

### Browser Support

- Chrome/Edge 90+
- Firefox 88+
- Safari 14+
- Mobile browsers (iOS Safari, Chrome Mobile)

---

For more information, see [Architecture](architecture.md) documentation.
