# Boxle AI - UI Redesign

This is the frontend UI for Boxle AI (forked from Bytebot), extracted for redesign in Bolt.new.

## Tech Stack

- **Next.js 14+** (App Router)
- **Tailwind CSS**
- **shadcn/ui** components
- **Socket.io** for WebSocket
- **react-vnc** for desktop viewer

## Redesign Goals

1. **Rebrand**: "Bytebot" → "Boxle AI"
2. **Layout**: Transform from tabbed pages to overlay/chat style
3. **Chat**: Add persistent slide-out or corner chat panel
4. **Desktop View**: Integrate with chat, not as separate tab
5. **Color Scheme**: Replace bronze palette with Boxle branding

## Critical Files - DO NOT MODIFY

These files contain the API contract with the backend:

```
src/utils/taskUtils.ts    - All API calls
src/hooks/useWebSocket.ts - WebSocket events
src/types/index.ts        - TypeScript types
```

## Files to Redesign

### Pages (`src/app/`)
- `page.tsx` - Home/task creation
- `tasks/page.tsx` - Task list  
- `tasks/[id]/page.tsx` - Task detail view
- `desktop/page.tsx` - Desktop viewer
- `layout.tsx` - Root layout
- `globals.css` - Styles (replace `--color-bytebot-*` variables)

### Components (`src/components/`)
- `layout/Header.tsx` - Navigation, branding
- `messages/*` - Chat components
- `tasks/*` - Task list components
- `vnc/VncViewer.tsx` - Desktop stream
- `ui/*` - shadcn components (restyle as needed)

## API Endpoints (Backend)

The UI calls these endpoints - don't change the API calls:

```
POST   /tasks              - Create task
GET    /tasks              - List tasks
GET    /tasks/:id          - Get task
POST   /tasks/:id/messages - Add message
POST   /tasks/:id/takeover - User takes control
POST   /tasks/:id/resume   - AI takes control
```

## WebSocket Events

```
join_task / leave_task    - Room subscription
task_updated              - Task status changed
new_message               - New chat message
```

## Development

```bash
npm install
npm run dev
```

## Environment Variables

```env
NEXT_PUBLIC_AGENT_URL=http://localhost:9991
NEXT_PUBLIC_DESKTOP_URL=http://localhost:9990
```

