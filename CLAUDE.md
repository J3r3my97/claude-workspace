# Global Claude Code Instructions

## Session Behavior
- Always start in plan mode
- Provide high-level explanations for each change made

## Code Philosophy
- Keep every change as simple as possible
- Minimize the scope of changes — touch as little code as necessary
- Avoid complex or sweeping refactors
- Simplicity above all else

## Never Do This
- Never speculate about code you haven't opened and read
- Never assume file contents — always read first


## Verification
- After making changes, always verify your work before considering the task done
- Run the relevant tests (`pytest`)
- Run the linter (`ruff check`)
- If it's a FastAPI endpoint, test it with `curl` or check the `/docs` page
- If something fails, fix it before moving on

## Tech Stack
### Backend
- Python with FastAPI
- Always dockerize for easy deployment and testing
- Use `uv` for dependency management
- Use `ruff` for linting

### Frontend
- Use whatever is optimal for the task

## Debugging Techniques

### Timing Instrumentation for Latency Issues
When investigating slow response times or latency issues (e.g., API calls, streaming, DB operations):
1. Add `console.log` timestamps at key checkpoints with `Date.now() - startTime`
2. Track both frontend (browser console) and backend (server logs) timing
3. Look for gaps between checkpoints to identify the bottleneck
4. Example pattern:
```typescript
const startTime = Date.now();
console.log(`[PREFIX] Step 1`);
// ... operation ...
console.log(`[PREFIX] Step 2: +${Date.now() - startTime}ms`);
```
This technique helped identify a 20s latency issue was caused by Dify using an unpublished GPT workflow instead of the faster Qwen model.

## Mistakes Log
<!-- When Claude makes a mistake, document it here so we avoid it in future sessions -->


