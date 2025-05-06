# Jotion - A Notion Clone

<div align="center">
  <img src="public/logo.svg" alt="Jotion Logo" width="100" height="100" style="background-color: white; padding: 10px; border-radius: 10px;"/>
  <h3>Your connected workspace for notes, documents, and collaborative editing</h3>
  
  [Live Demo](https://jotion-theta.vercel.app) | [Repository](https://github.com/Arshnoor-Singh-Sohi/Jotion)

  ![Next.js](https://img.shields.io/badge/Next.js-14.0.1-black)
  ![Convex](https://img.shields.io/badge/Convex-1.5.1-blue)
  ![TailwindCSS](https://img.shields.io/badge/TailwindCSS-3.3.0-06B6D4)
  ![Clerk](https://img.shields.io/badge/Clerk-4.27.2-6C47FF)
  ![TypeScript](https://img.shields.io/badge/TypeScript-5.0.0-3178C6)
</div>

## 📋 Table of Contents

- [Introduction](#-introduction)
- [Features](#-features)
- [System Architecture](#-system-architecture)
- [Technologies](#-technologies)
- [Project Structure](#-project-structure)
- [Core Components](#-core-components)
  - [Authentication](#authentication)
  - [Document Management](#document-management)
  - [Real-time Collaboration](#real-time-collaboration)
  - [Rich Text Editor](#rich-text-editor)
  - [UI Components](#ui-components)
- [Data Flow](#-data-flow)
- [Design Patterns](#-design-patterns)
- [State Management](#-state-management)
- [Routing](#-routing)
- [Installation & Setup](#-installation--setup)
- [Deployment](#-deployment)
- [Best Practices](#-best-practices)
- [Future Enhancements](#-future-enhancements)
- [Contributing](#-contributing)
- [License](#-license)

## 🚀 Introduction

Jotion is a powerful Notion-inspired workspace that combines document editing, organization, and real-time collaboration in one seamless application. Built with modern web technologies like Next.js, Convex, and TailwindCSS, Jotion provides an intuitive interface for managing documents, notes, and collaborative content.

This project demonstrates the implementation of complex features such as real-time database updates, rich text editing, hierarchical document management, and public document sharing - all with a clean, responsive interface that works across different devices.

## ✨ Features

### Core Functionality

- **📝 Rich Document Editing**: Full-featured editor with formatting, headings, lists, and more powered by BlockNote
- **🌲 Hierarchical Organization**: Organize documents in nested structures
- **🔄 Real-time Updates**: Changes sync instantly across all connected clients
- **🔍 Powerful Search**: Quickly find documents with the command palette (⌘K)
- **🌓 Light/Dark Mode**: Support for both light and dark themes

### Document Management

- **🆕 Document Creation**: Create new documents with customizable titles
- **📂 Document Organization**: Nested document organization with infinite depth
- **🗑️ Trash Management**: Archive and restore documents
- **🔒 Document Privacy**: Private by default with option to publish

### Customization

- **🖼️ Cover Images**: Add and customize document cover images
- **😀 Icons**: Add emoji icons to documents for visual organization
- **🎨 Theming**: Switch between light and dark mode

### Collaboration

- **🔗 Shareable Links**: Generate public links for document sharing
- **👥 Multi-User Access**: Authentication system for user-specific document access
- **🔄 Real-time Collaboration**: See changes from other users in real-time

## 🏗 System Architecture

Jotion follows a modern web application architecture with several key components:

```
┌───────────────────┐     ┌───────────────────┐     ┌───────────────────┐
│                   │     │                   │     │                   │
│  Client (Browser) │◄────┤   Next.js Server  │◄────┤   Convex Backend  │
│                   │     │                   │     │                   │
└───────────────────┘     └───────────────────┘     └───────────────────┘
         ▲                                                   ▲
         │                                                   │
         │                                                   │
         │                        ┌───────────────────┐      │
         │                        │                   │      │
         └────────────────────────┤  EdgeStore Files  │◄─────┘
                                  │                   │
                                  └───────────────────┘
```

### Architecture Components

1. **Client**: React-based frontend rendered with Next.js
2. **Next.js Server**: Handles routing, server components, and API endpoints
3. **Convex Backend**: Real-time database and backend functionality
4. **EdgeStore**: File storage for document cover images and attachments
5. **Clerk**: Authentication service (not shown in diagram but integrated with the client)

### Data Flow

```
┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│ User Interface│     │ React State   │     │ Data Mutation │
│ Components    │────►│ (Zustand)     │────►│ (Convex)      │
└───────────────┘     └───────────────┘     └───────────────┘
                                                    │
                                                    ▼
┌───────────────┐     ┌───────────────┐     ┌───────────────┐
│ UI Updates    │◄────│ React State   │◄────│ Data Query    │
│               │     │ (Zustand)     │     │ (Convex)      │
└───────────────┘     └───────────────┘     └───────────────┘
```

## 🛠 Technologies

Jotion is built with a modern tech stack:

### Frontend
- **Next.js**: React framework for server-side rendering and routing
- **TailwindCSS**: Utility-first CSS framework
- **Shadcn UI**: Component library built on Radix UI primitives
- **React**: JavaScript library for building user interfaces
- **TypeScript**: Static typing for JavaScript
- **Zustand**: Lightweight state management library
- **BlockNote**: Rich text editor component
- **cmdk**: Command menu component
- **Lucide React**: Icon library
- **React Dropzone**: File upload utility
- **Next Themes**: Theme management for Next.js

### Backend
- **Convex**: Real-time database and backend service
- **EdgeStore**: File storage service
- **Clerk**: Authentication provider

### Development Tools
- **ESLint**: JavaScript linting utility
- **PostCSS**: CSS transformation tool
- **Autoprefixer**: CSS vendor prefixing tool

## 📂 Project Structure

Jotion follows a well-organized project structure:

```
jotion/
├── app/                  # Next.js application routes
│   ├── (main)/           # Main app routes (authenticated)
│   ├── (marketing)/      # Marketing/landing pages
│   ├── (public)/         # Public document viewing
│   ├── api/              # API routes
│   └── globals.css       # Global CSS styles
├── components/           # React components
│   ├── modals/           # Modal components
│   ├── providers/        # Context providers
│   ├── ui/               # UI components (shadcn)
│   └── ...               # Other shared components
├── convex/               # Convex database and API
│   ├── documents.ts      # Document operations
│   └── schema.ts         # Database schema
├── hooks/                # Custom React hooks
├── lib/                  # Utility functions
├── public/               # Static assets
└── ...                   # Config files
```

### Key Directories and Files

- **app/**: Contains all Next.js pages and routes using the App Router
- **components/**: Reusable React components
- **convex/**: Backend database schema and operations
- **hooks/**: Custom React hooks for state management
- **lib/**: Utility functions and services
- **public/**: Static assets like images and icons

## 💻 Core Components

### Authentication

Authentication in Jotion is handled by Clerk, a complete authentication and user management service. The implementation includes:

```typescript
// ConvexClientProvider component handles authentication setup
export const ConvexClientProvider = ({
    children
}: {
    children: ReactNode;
}) => {
    return (
        <ClerkProvider
            publishableKey={process.env.NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY!}
        >
            <ConvexProviderWithClerk
                useAuth={useAuth}
                client={convex}
            >
                {children}
            </ConvexProviderWithClerk>
        </ClerkProvider>
    );
};
```

The authentication flow works as follows:

1. **User Sign-up/Login**: Users can sign up or log in via the marketing page
2. **Authentication State**: Clerk handles authentication state
3. **Protected Routes**: Main application routes are protected using the authentication state
4. **User Identity**: Convex backend receives user identity for data access control

### Document Management

Document management is a core feature of Jotion, with operations defined in the Convex backend:

#### Document Schema

```typescript
// Document schema in convex/schema.ts
export default defineSchema({
    documents: defineTable({
        title: v.string(),
        userId: v.string(),
        isArchived: v.boolean(),
        parentDocument: v.optional(v.id("documents")),
        content: v.optional(v.string()),
        coverImage: v.optional(v.string()),
        icon: v.optional(v.string()),
        isPublished: v.boolean(),
    })
        .index("by_user", ["userId"])
        .index("by_user_parent", ["userId", "parentDocument"])
});
```

#### Document Operations

The following operations are implemented for document management:

- **Create**: Create new documents
- **Update**: Update document title, content, icon, cover image
- **Archive**: Move documents to trash
- **Restore**: Restore documents from trash
- **Delete**: Permanently delete documents
- **Publish/Unpublish**: Make documents publicly accessible

### Real-time Collaboration

Real-time collaboration is enabled through Convex's real-time database capabilities:

1. **Data Synchronization**: Convex automatically synchronizes data changes across clients
2. **Optimistic Updates**: UI updates immediately while changes are sent to the server
3. **Conflict Resolution**: Convex handles conflict resolution for concurrent edits

### Rich Text Editor

The rich text editing experience is powered by BlockNote:

```typescript
// Editor component
const Editor = ({
    onChange,
    initialContent,
    editable
}: EditorProps) => {
    const { resolvedTheme } = useTheme();
    const { edgestore } = useEdgeStore();

    // Handle file uploads
    const handleUpload = async (file: File) => {
        const response = await edgestore.publicFiles.upload({
            file
        });
        return response.url;
    }

    // Initialize the editor
    const editor: BlockNoteEditor = useBlockNote({
        editable,
        initialContent: initialContent
            ? JSON.parse(initialContent) as PartialBlock[]
            : undefined,
        onEditorContentChange: (editor) => {
            onChange(JSON.stringify(editor.topLevelBlocks, null, 2));
        },
        uploadFile: handleUpload
    })

    return (
        <div>
            <BlockNoteView
                editor={editor}
                theme={resolvedTheme === "dark" ? "dark" : "light"}
            />
        </div>
    )
}
```

The editor provides:

- **Rich Text Formatting**: Bold, italic, underline, etc.
- **Block Elements**: Headings, lists, code blocks, etc.
- **File Uploads**: Support for images and other file attachments
- **Theme Support**: Adaptive to light/dark mode

### UI Components

Jotion uses a combination of custom components and shadcn UI components for a cohesive user interface:

#### Navigation

The navigation system includes:

- **Sidebar**: Shows document structure with collapsible tree
- **Toolbar**: Document-specific actions and formatting
- **Command Menu**: Quick navigation and search (⌘K)

#### Modals

Modal dialogs for various actions:

- **SettingsModal**: Application settings
- **CoverImageModal**: Upload and manage document cover images

#### Theme Support

Theme management with Next Themes:

```typescript
// ThemeProvider component
export function ThemeProvider({ children, ...props }: ThemeProviderProps) {
    return <NextThemesProvider {...props}>{children}</NextThemesProvider>
}
```

## 📊 Data Flow

### Creating and Updating Documents

The data flow for document operations follows this pattern:

1. **User Interaction**: User creates or updates a document
2. **UI State Update**: Local state is updated via Zustand
3. **API Call**: Convex mutation is called to update the database
4. **Database Update**: Document is saved in Convex
5. **Real-time Update**: Changes are broadcast to all connected clients
6. **UI Refresh**: UI components update to reflect the changes

### Document Hierarchy

Documents are organized in a hierarchical structure:

```
Root Documents
├── Document 1
│   ├── Subdocument 1.1
│   └── Subdocument 1.2
├── Document 2
└── Document 3
    └── Subdocument 3.1
        └── Subdocument 3.1.1
```

This is implemented using the `parentDocument` field in the document schema, which references another document ID.

## 🧩 Design Patterns

### Component Composition

Jotion extensively uses component composition for reusable UI elements. For example, the document list is composed of individual item components:

```tsx
// DocumentList component using Item components
export const DocumentList = ({
    parentDocumentId,
    level = 0
}: DocumentListProps) => {
    // ...
    return (
        <>
            {documents.map((document) => (
                <div key={document._id}>
                    <Item
                        id={document._id}
                        onClick={() => onRedirect(document._id)}
                        label={document.title}
                        icon={FileIcon}
                        documentIcon={document.icon}
                        active={params.documentId === document._id}
                        level={level}
                        onExpand={() => onExpand(document._id)}
                        expanded={expanded[document._id]}
                    />
                    {expanded[document._id] && (
                        <DocumentList
                            parentDocumentId={document._id}
                            level={level + 1}
                        />
                    )}
                </div>
            ))}
        </>
    );
};
```

### Custom Hooks

Custom hooks are used to encapsulate and reuse logic across components:

```typescript
// useCoverImage hook for managing cover image state
export const useCoverImage = create<CoverImageStore>((set) => ({
    url: undefined,
    isOpen: false,
    onOpen: () => set({ isOpen: true, url: undefined }),
    onClose: () => set({ isOpen: false, url: undefined }),
    onReplace: (url: string) => set({ isOpen: true, url })
}));
```

### Server/Client Components

Next.js 14's approach to server and client components is utilized:

- **Server Components**: Used for data fetching and rendering static content
- **Client Components**: Used for interactive elements with "use client" directive

```typescript
// Client component example
"use client";

import { useTheme } from "next-themes";
// ... other imports

const Editor = ({ /* ... */ }) => {
    const { resolvedTheme } = useTheme();
    // ... component implementation
}
```

## 🧠 State Management

Jotion uses a combination of state management approaches:

### Zustand

Zustand is used for global UI state management with custom stores:

```typescript
// Search store example
type SearchStore = {
    isOpen: boolean;
    onOpen: () => void;
    onClose: () => void;
    toggle: () => void;
};

export const useSearch = create<SearchStore>((set, get) => ({
    isOpen: false,
    onOpen: () => set({ isOpen: true }),
    onClose: () => set({ isOpen: false }),
    toggle: () => set({ isOpen: !get().isOpen }),
}));
```

### Convex State

Convex provides real-time state management for database-related state:

```typescript
// Using Convex queries for real-time data
const documents = useQuery(api.documents.getSidebar, {
    parentDocument: parentDocumentId
});
```

### React State

Local component state is used where appropriate:

```typescript
const [expanded, setExpanded] = useState<Record<string, boolean>>({});

const onExpand = (documentId: string) => {
    setExpanded(prevExpanded => ({
        ...prevExpanded,
        [documentId]: !prevExpanded[documentId]
    }));
};
```

## 🔀 Routing

Jotion uses Next.js App Router for advanced routing capabilities:

### Route Groups

The app directory is organized using route groups:

```
app/
├── (main)/           # Authenticated routes
├── (marketing)/      # Public marketing pages
└── (public)/         # Public document routes
```

### Dynamic Routes

Dynamic routes are used for document pages:

```
app/
├── (main)/
│   └── (routes)/
│       └── documents/
│           └── [documentId]/
│               └── page.tsx  # Dynamic document page
└── (public)/
    └── (routes)/
        └── preview/
            └── [documentId]/
                └── page.tsx  # Public document preview
```

### Navigation

Navigation is handled using Next.js's built-in capabilities and the Routemaster library for programmatic navigation:

```typescript
// Programmatic navigation example
const onRedirect = (documentId: string) => {
    router.push(`/documents/${documentId}`);
};
```

## 🚀 Installation & Setup

Follow these steps to set up Jotion locally:

### Prerequisites

- Node.js 18+ and npm/yarn
- Convex account
- Clerk account
- EdgeStore account

### Installation Steps

1. **Clone the repository**

```bash
git clone https://github.com/Arshnoor-Singh-Sohi/Jotion.git
cd Jotion
```

2. **Install dependencies**

```bash
npm install
# or
yarn install
```

3. **Set up environment variables**

Create a `.env.local` file with the following variables:

```
# Clerk (Authentication)
NEXT_PUBLIC_CLERK_PUBLISHABLE_KEY=your_clerk_publishable_key
CLERK_SECRET_KEY=your_clerk_secret_key

# Convex (Database)
NEXT_PUBLIC_CONVEX_URL=your_convex_url

# EdgeStore (File Storage)
EDGE_STORE_ACCESS_KEY=your_edgestore_access_key
EDGE_STORE_SECRET_KEY=your_edgestore_secret_key
```

4. **Set up Convex**

```bash
npx convex dev
```

5. **Start the development server**

```bash
npm run dev
# or
yarn dev
```

6. **Open your browser**

Navigate to [http://localhost:3000](http://localhost:3000) to see the application.

## 🌐 Deployment

Jotion can be deployed using Vercel for the frontend and Convex for the backend:

### Vercel Deployment

1. Push your code to a GitHub repository
2. Connect the repository to Vercel
3. Configure environment variables
4. Deploy the application

### Convex Deployment

1. Run `npx convex deploy` to deploy your Convex functions
2. Update the `NEXT_PUBLIC_CONVEX_URL` environment variable in Vercel

## 🏆 Best Practices

Jotion follows several best practices:

### Code Organization

- **Component Structure**: Components are organized by feature and responsibility
- **Type Safety**: TypeScript is used throughout the project
- **Custom Hooks**: Logic is encapsulated in reusable hooks

### Performance Optimization

- **Next.js Optimizations**: Image optimization, code splitting, etc.
- **Lazy Loading**: Components like the editor are loaded dynamically
- **Efficient Queries**: Convex queries are optimized with proper indexing

### User Experience

- **Responsive Design**: Works on mobile, tablet, and desktop
- **Accessibility**: Proper ARIA attributes and keyboard navigation
- **Error Handling**: Graceful error handling with feedback to users

## 🔮 Future Enhancements

Possible future enhancements for Jotion:

- **Collaborative Cursors**: Show other users' cursors in real-time
- **Comments & Discussions**: Add commenting functionality
- **Templates**: Document templates for common use cases
- **Advanced Permissions**: Fine-grained access control
- **Integrations**: Connect with other services like Slack, Google Drive, etc.
- **Export Options**: Export documents in various formats (PDF, Markdown, etc.)

## 🤝 Contributing

Contributions to Jotion are welcome! To contribute:

1. Fork the repository
2. Create a feature branch (`git checkout -b feature/amazing-feature`)
3. Commit your changes (`git commit -m 'Add amazing feature'`)
4. Push to the branch (`git push origin feature/amazing-feature`)
5. Open a Pull Request

## 📄 License

This project is licensed under the MIT License - see the LICENSE file for details.

---

<div align="center">
  <p>Built with ❤️ by <a href="https://github.com/Arshnoor-Singh-Sohi">Arshnoor Singh Sohi</a></p>
</div>
