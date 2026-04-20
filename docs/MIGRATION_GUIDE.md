# Migration Guide for Pending Features

> Generated from open pull requests in the repository.

---

## PR #5: HOTFIX: Critical memory optimization for issues #49 and #46

**Pull Request:** [#5](https://github.com/moyanGmail/MrGGLS-claude-code/pull/5)  
**Author:** moyanGmail  
**Branch:** `hotfix/memory-optimization-v1.0.72` → `main`

### Summary of Changes

This **v1.0.72 hotfix** introduces critical memory optimization and context management fixes to address severe stability issues affecting the Claude Code tool. The PR adds a new documentation file — `docs/MEMORY_OPTIMIZATION.md` — and implements fixes for:

- **Issue #49**: Context auto-compact stuck at 0%, rendering the tool unusable on macOS.
- **Issue #46**: JavaScript **heap exhaustion** during large MCP operations causing complete crashes.

Key technical changes include:
1. Progressive context cleanup with configurable thresholds.
2. Streaming data processing to prevent heap exhaustion.
3. Memory usage monitoring and automatic pruning.
4. Garbage collection optimization for large operations.

### New Configuration or Environment Variables

The PR introduces the following configuration options (documented in `docs/MEMORY_OPTIMIZATION.md`):

```json
{
  "memory": {
    "contextBufferLimit": "10MB",
    "autoCompactThreshold": 0.8,
    "streamingChunkSize": "1MB",
    "gcOptimization": true
  }
}
```

### Installation or Usage Instructions

1. **Immediate fixes after merge:**
   - The default **context buffer limit** is set to `10MB`.
   - **Automatic context pruning** triggers at `80%` threshold (`autoCompactThreshold: 0.8`).
   - Large MCP operations are automatically streamed in `1MB` chunks.

2. **Manual commands:**
   - Use the `/memory-reset` command to manually reset the context buffer if memory issues persist.

3. **Monitoring:**
   - Memory usage monitoring and alerts are enabled automatically when `gcOptimization` is set to `true`.

4. **Documentation:**
   - Refer to `docs/MEMORY_OPTIMIZATION.md` for comprehensive root-cause analysis, impact assessments, and additional configuration examples.
