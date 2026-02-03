# Architecture

Understanding DevRead.me's architecture helps you better utilize and extend the application.

## System Overview

```
┌─────────────────────────────────────────────────────────────┐
│                        Frontend Layer                        │
│              (React 18.2 + Next.js 14 + TypeScript)        │
│                                                              │
│  ┌──────────────────────────────────────────────────────┐  │
│  │              User Interface Components               │  │
│  │  - Form input and validation                         │  │
│  │  - Color picker                                      │  │
│  │  - Configuration options                             │  │
│  │  - Progress tracking display                         │  │
│  │  - Animated backgrounds                              │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                             │
                             ↓
┌─────────────────────────────────────────────────────────────┐
│                      API Layer                               │
│              (Next.js API Routes)                            │
│                                                              │
│  ┌──────────────────────────────────────────────────────┐  │
│  │            POST /api/generate                        │  │
│  │  - Request validation                                │  │
│  │  - Parameters processing                             │  │
│  │  - Service orchestration                             │  │
│  │  - Response formatting                               │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
                             │
                             ↓
┌─────────────────────────────────────────────────────────────┐
│                   Service Layer                              │
│            (Business Logic & Processing)                     │
│                                                              │
│  ┌─────────────────┐  ┌─────────────────┐  ┌────────────┐ │
│  │  Groq Service   │  │   Template      │  │   Export   │ │
│  │                 │  │   Processor     │  │   Service  │ │
│  │ - AI Integration│  │                 │  │            │ │
│  │ - Prompt Build  │  │ - File Process  │  │ - ZIP Pack │ │
│  │ - Stream Handle │  │ - Customization │  │ - Compress │ │
│  │ - Error Handle  │  │ - Variable Sub  │  │ - Validate │ │
│  └─────────────────┘  └─────────────────┘  └────────────┘ │
└─────────────────────────────────────────────────────────────┘
                             │
                             ↓
┌─────────────────────────────────────────────────────────────┐
│                 External Services                            │
│                                                              │
│  ┌──────────────────────────────────────────────────────┐  │
│  │         Groq Cloud API - Llama 3.3 70B              │  │
│  │  - Advanced language model                           │  │
│  │  - Token streaming                                   │  │
│  │  - High-performance inference                        │  │
│  └──────────────────────────────────────────────────────┘  │
└─────────────────────────────────────────────────────────────┘
```

## Directory Structure

```
devreadme/
├── app/
│   ├── page.tsx              # Main UI component
│   ├── layout.tsx            # Root layout
│   ├── globals.css           # Global styles
│   └── api/
│       └── generate/
│           └── route.ts      # API endpoint
│
├── lib/
│   ├── groq-service.ts       # AI integration
│   ├── template-processor.ts # File processing
│   ├── export-service.ts     # ZIP creation
│   └── api-utils.ts          # Helper functions
│
├── components/
│   ├── FormInput.tsx         # Form component
│   ├── ColorPicker.tsx       # Color selection
│   ├── ProgressBar.tsx       # Generation progress
│   └── OptionSelector.tsx    # Configuration UI
│
├── public/
│   ├── img/                  # Images and assets
│   └── styles/               # Additional styles
│
├── docs/
│   └── [documentation files]
│
└── package.json              # Dependencies
```

## Component Architecture

### Frontend Components

#### Page Component (page.tsx)

The main entry point handling:

```typescript
export default function Home() {
  // State management
  const [content, setContent] = useState('');
  const [options, setOptions] = useState({...});
  const [isLoading, setIsLoading] = useState(false);
  const [progress, setProgress] = useState(0);

  // Form submission
  const handleGenerate = async () => {...};

  // UI rendering
  return <div>...</div>;
}
```

**Responsibilities:**

- User input collection
- Form validation
- API communication
- Progress tracking
- Download handling

#### Layout Component (layout.tsx)

```typescript
export default function RootLayout({ children }) {
  return (
    <html>
      <head>{/* metadata */}</head>
      <body>{children}</body>
    </html>
  );
}
```

**Responsibilities:**

- Page structure
- Metadata management
- Global styles
- Font loading

#### UI Components

Individual React components for:

- Form inputs
- Color picker
- Option selectors
- Progress indicators
- Error displays

## Service Architecture

### Groq Service (groq-service.ts)

```typescript
class GroqService {
  async generateDocumentation(
    content: string,
    options: GenerationOptions,
  ): Promise<DocumentationFiles> {
    // 1. Build system prompt
    // 2. Create user message
    // 3. Call Groq API
    // 4. Stream response
    // 5. Parse content
    // 6. Return files
  }

  private buildPrompt(content: string): string {
    // Construct AI prompt for documentation
  }

  private parseResponse(response: string): DocumentationFiles {
    // Extract markdown files from response
  }
}
```

**Key Methods:**

- `generateDocumentation()` - Main generation method
- `buildPrompt()` - Construct AI prompt
- `parseResponse()` - Extract generated files
- `handleStream()` - Process streaming response

### Template Processor (template-processor.ts)

```typescript
class TemplateProcessor {
  processTemplate(template: string, variables: Record<string, any>): string {
    // Replace variables in template
  }

  applyCustomization(
    files: DocumentationFiles,
    customization: CustomizationOptions,
  ): DocumentationFiles {
    // Apply color, design, sidebar options
  }

  generateIndexHtml(options: GenerationOptions): string {
    // Create Docsify index.html
  }

  generateSidebar(files: DocumentationFiles): string {
    // Create _sidebar.md
  }
}
```

**Key Methods:**

- `processTemplate()` - Template variable substitution
- `applyCustomization()` - Apply user preferences
- `generateIndexHtml()` - Create Docsify config
- `generateSidebar()` - Create navigation file

### Export Service (export-service.ts)

```typescript
class ExportService {
  async createZipPackage(
    files: DocumentationFiles,
    options: ZipOptions,
  ): Promise<Buffer> {
    // 1. Create JSZip instance
    // 2. Add all files
    // 3. Compress
    // 4. Validate
    // 5. Return buffer
  }

  private validateBundle(zip: JSZip): boolean {
    // Verify bundle integrity
  }

  private optimizeFiles(files: DocumentationFiles): void {
    // Minify CSS, optimize images
  }
}
```

**Key Methods:**

- `createZipPackage()` - Create downloadable ZIP
- `validateBundle()` - Verify contents
- `optimizeFiles()` - Compress output

## Data Flow

### Generation Process

```
1. User Input
   ↓
2. Form Validation
   ↓
3. API Request
   ↓
4. Groq Service
   ├─ Build Prompt
   ├─ Call Groq API
   ├─ Stream Response
   └─ Parse Files
   ↓
5. Template Processor
   ├─ Apply Theme
   ├─ Apply Layout
   └─ Generate Config Files
   ↓
6. Export Service
   ├─ Create ZIP
   ├─ Validate Package
   └─ Generate Download URL
   ↓
7. User Download
```

### Request Flow

```json
POST /api/generate
{
  "content": "project description",
  "options": {
    "color": "#10b981",
    "includeSidebar": true,
    "designVersion": "v2",
    "outputFormat": "full"
  }
}
```

### Response Flow

```json
{
  "success": true,
  "data": {
    "files": [
      { "name": "README.md", "content": "..." },
      { "name": "SETUP.md", "content": "..." },
      ...
    ],
    "zipUrl": "https://..."
  }
}
```

## Technology Stack Integration

### Frontend Stack

```
User Browser
    ↓
React 18.2 (UI Framework)
    ↓
Next.js 14 (React Framework)
    ↓
TypeScript 5.3 (Type Safety)
    ↓
Tailwind CSS (Styling)
    ↓
Framer Motion (Animations)
    ↓
Lucide Icons (Icons)
```

### Backend Stack

```
API Route (route.ts)
    ↓
Node.js Runtime
    ↓
Groq SDK (AI Integration)
    ↓
JSZip (ZIP Creation)
    ↓
File System (Output)
```

### External Services

```
Groq Cloud API
├─ Model: Llama 3.3 70B
├─ Protocol: OpenAI-compatible
├─ Format: Streaming JSON
└─ Auth: API Key
```

## Security Architecture

### Input Validation

```
User Input
    ↓
Length Check (50+ chars)
    ↓
Character Encoding (UTF-8)
    ↓
Injection Prevention
    ↓
Schema Validation
    ↓
Sanitization
```

### API Security

```
Request
    ↓
HTTPS Only
    ↓
Rate Limiting
    ↓
Authentication
    ↓
Groq API Key (Secure)
    ↓
Response
```

### Data Privacy

- **No Permanent Storage**: Data processed and discarded
- **No Training Data**: Input not used to train models
- **Session-Based**: Per-request isolation
- **Secure Communication**: HTTPS encryption

## Performance Optimization

### Frontend Optimization

- **Code Splitting**: Lazy-loaded components
- **Image Optimization**: Next.js Image component
- **CSS Optimization**: Tailwind purging
- **Caching**: Browser caching headers

### API Optimization

- **Streaming Response**: Real-time token generation
- **Connection Pooling**: Reusable API connections
- **Response Compression**: Gzip compression
- **Parallel Processing**: Async/await patterns

### Generation Optimization

- **Prompt Optimization**: Efficient token usage
- **Streaming Processing**: Incremental generation
- **Template Caching**: Pre-compiled templates
- **ZIP Compression**: Optimized file sizes

## Error Handling

### Error Types

```
User Error (4xx)
├─ Invalid Input (400)
├─ Rate Limited (429)
└─ Not Found (404)

Server Error (5xx)
├─ Generation Failed (500)
├─ API Error (502)
└─ Service Unavailable (503)
```

### Error Recovery

```
Error Occurs
    ↓
Log Error Details
    ↓
Return User-Friendly Message
    ↓
Suggest Solutions
    ↓
Allow Retry
```

## Scalability Considerations

### Horizontal Scaling

- Stateless API design
- Load balancing ready
- Distributed generation
- Shared storage for outputs

### Vertical Scaling

- Efficient memory usage
- Optimized algorithms
- Resource pooling
- Connection management

## Future Architecture Plans

- [ ] User authentication system
- [ ] Project history/storage
- [ ] Template customization API
- [ ] Batch processing
- [ ] Webhook notifications
- [ ] Rate limit management
- [ ] Analytics integration
- [ ] Custom integrations

---

For implementation details, see [Tech Stack](tech-stack.md) documentation.
