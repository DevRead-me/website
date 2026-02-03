# API Documentation

DevRead.me is primarily a web-based application, but this documentation describes how it works for developers interested in understanding the system.

## Overview

DevRead.me consists of a Next.js frontend with API routes that handle documentation generation using the Groq API.

## API Endpoints

### Generate Documentation

**Endpoint:** `/api/generate`

**Method:** `POST`

**Purpose:** Generates documentation based on provided input

#### Request

```json
{
  "content": "string",
  "options": {
    "color": "string (hex color)",
    "includeSidebar": "boolean",
    "designVersion": "v1 | v2",
    "outputFormat": "full | readme"
  }
}
```

**Parameters:**

| Parameter        | Type    | Description                                    |
| ---------------- | ------- | ---------------------------------------------- |
| `content`        | string  | Your project README or description             |
| `color`          | string  | Hex color code (e.g., "#10b981")               |
| `includeSidebar` | boolean | Include navigation sidebar                     |
| `designVersion`  | string  | Choose V1 or V2 design                         |
| `outputFormat`   | string  | "full" for Docsify or "readme" for single file |

#### Response

```json
{
  "success": true,
  "data": {
    "files": [
      {
        "name": "README.md",
        "content": "..."
      },
      {
        "name": "SETUP.md",
        "content": "..."
      }
    ],
    "zipUrl": "string"
  }
}
```

#### Example Request

```bash
curl -X POST https://devread.me/api/generate \
  -H "Content-Type: application/json" \
  -d '{
    "content": "My awesome project that does X, Y, and Z",
    "options": {
      "color": "#10b981",
      "includeSidebar": true,
      "designVersion": "v2",
      "outputFormat": "full"
    }
  }'
```

#### Status Codes

| Code | Meaning                     |
| ---- | --------------------------- |
| 200  | Success                     |
| 400  | Bad request (invalid input) |
| 429  | Rate limited                |
| 500  | Server error                |

## Groq API Integration

DevRead.me uses the Groq Cloud API for AI-powered generation.

### Authentication

The API authenticates with Groq using an API key stored in environment variables:

```
GROQ_API_KEY=your_api_key_here
```

### Model Used

- **Model ID:** `llama-3.3-70b-versatile`
- **Base URL:** `https://api.groq.com/openai/v1`

### Request Format

Requests follow OpenAI API compatibility:

```javascript
const response = await groq.chat.completions.create({
  model: "llama-3.3-70b-versatile",
  messages: [
    {
      role: "system",
      content: "You are a professional documentation writer...",
    },
    {
      role: "user",
      content: userInput,
    },
  ],
  stream: true,
  temperature: 0.7,
  max_tokens: 2048,
});
```

### Streaming

Responses use streaming for real-time generation:

```javascript
for await (const chunk of response) {
  console.log(chunk.choices[0].delta.content);
}
```

## Service Architecture

### Groq Service

**File:** `lib/groq-service.ts`

**Purpose:** Handles AI integration and content generation

**Key Methods:**

```typescript
async generateDocumentation(
  content: string,
  options: GenerationOptions
): Promise<DocumentationFiles>
```

Handles:

- Prompt construction
- API communication
- Response streaming
- File generation

### Template Processor

**File:** `lib/template-processor.ts`

**Purpose:** Processes templates and customizes output

**Key Methods:**

```typescript
processTemplate(
  template: string,
  variables: Record<string, any>
): string

applyCustomization(
  files: DocumentationFiles,
  customization: CustomizationOptions
): DocumentationFiles
```

### Export Service

**File:** `lib/export-service.ts`

**Purpose:** Creates ZIP packages for download

**Key Methods:**

```typescript
createZipPackage(
  files: DocumentationFiles,
  options: ZipOptions
): Promise<Buffer>
```

Handles:

- ZIP file creation
- File compression
- Asset inclusion
- Integrity verification

### API Utils

**File:** `lib/api-utils.ts`

**Purpose:** Helper functions for API operations

**Utilities:**

- Input validation
- Error handling
- Response formatting
- Logging

## Response Examples

### Full Documentation Response

```json
{
  "success": true,
  "data": {
    "files": [
      {
        "name": "README.md",
        "content": "# Project Title\n\nProject description..."
      },
      {
        "name": "SETUP.md",
        "content": "# Setup Instructions\n\n1. Install..."
      },
      {
        "name": "API.md",
        "content": "# API Documentation\n\n## Endpoints..."
      },
      {
        "name": "FEATURES.md",
        "content": "# Features\n\nKey features include..."
      },
      {
        "name": "TROUBLESHOOTING.md",
        "content": "# Troubleshooting\n\n## Common Issues..."
      }
    ],
    "zipUrl": "https://devread.me/downloads/docs_12345.zip"
  }
}
```

### Error Response

```json
{
  "success": false,
  "error": {
    "code": "INVALID_INPUT",
    "message": "Content is too short or empty",
    "details": {
      "field": "content",
      "reason": "Minimum 50 characters required"
    }
  }
}
```

## Rate Limiting

DevRead.me implements rate limiting to prevent abuse:

### Limits

- **10 requests per hour** per IP address
- **100 requests per day** per IP address

### Headers

Responses include rate limit information:

```
X-RateLimit-Limit: 10
X-RateLimit-Remaining: 5
X-RateLimit-Reset: 1675000000
```

## Error Handling

### Common Errors

| Error                 | Cause             | Solution                    |
| --------------------- | ----------------- | --------------------------- |
| `INVALID_INPUT`       | Content too short | Provide more detailed input |
| `RATE_LIMIT_EXCEEDED` | Too many requests | Wait before trying again    |
| `API_ERROR`           | Groq API issue    | Retry after a few moments   |
| `GENERATION_FAILED`   | Generation failed | Check input quality         |

### Error Response Format

```json
{
  "success": false,
  "error": {
    "code": "ERROR_CODE",
    "message": "Human readable message",
    "timestamp": "2024-02-03T10:30:00Z",
    "requestId": "req_12345"
  }
}
```

## Performance Metrics

### Typical Timings

- **Generation**: 20-35 seconds
- **ZIP Creation**: 1-2 seconds
- **Total**: ~30 seconds

### File Sizes

- **Average Output**: 200-500 KB
- **ZIP Compressed**: 50-150 KB
- **Individual Files**: 5-50 KB each

## Security

### Authentication

- API routes require HTTPS
- No authentication currently required for frontend
- Rate limiting prevents abuse
- Input validation on all requests

### Data Privacy

- No permanent storage of input
- No data logging for AI training
- Secure API communication with Groq
- Session-based processing only

### Input Validation

All inputs are validated for:

- Length (minimum 50 characters)
- Character encoding (UTF-8)
- Injection attacks (escaped)
- Malformed content

## Development

For developers interested in extending DevRead.me:

### Environment Variables

```env
GROQ_API_KEY=your_api_key
NEXT_PUBLIC_APP_URL=http://localhost:3000
```

### Running Locally

```bash
# Install dependencies
npm install

# Set up environment
cp .env.example .env.local

# Run development server
npm run dev

# Access at http://localhost:3000
```

### API Testing

```bash
# Test the API endpoint
curl -X POST http://localhost:3000/api/generate \
  -H "Content-Type: application/json" \
  -d '{"content": "..."}'
```

## Best Practices

### For API Users

1. **Validate Input**: Provide quality, detailed content
2. **Handle Errors**: Implement proper error handling
3. **Respect Rate Limits**: Don't spam requests
4. **Use Streaming**: Handle responses properly
5. **Test Locally**: Verify before production use

### For Developers

1. **Error Handling**: Implement comprehensive error checks
2. **Logging**: Log important events for debugging
3. **Testing**: Write tests for API routes
4. **Documentation**: Keep API docs updated
5. **Version Control**: Track API changes

## Future API Features

- Authentication system
- User accounts and history
- Template customization API
- Batch processing
- Webhooks for async generation

---

**Questions about the API?** Check our [FAQ](../resources/faq.md) or [Contact Support](../resources/contact.md)
