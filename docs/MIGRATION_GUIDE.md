# Migration Guide for Pending Features

## HOTFIX: Critical memory optimization for issues #49 and #46 (PR #5)

### Summary of Changes
This **v1.0.72 hotfix** pull request introduces critical **memory optimization** and **context management** fixes to address severe stability issues affecting the Claude Code tool. The changes include:

- Resolution for **Issue #49**: Context auto-compact stuck at 0%, rendering the tool unusable on macOS.
- Resolution for **Issue #46**: JavaScript **heap exhaustion** during large MCP operations causing complete crashes.
- Progressive context cleanup with configurable thresholds.
- Streaming data processing to prevent heap exhaustion.
- Memory usage monitoring and automatic pruning.
- Updated documentation with configuration options and workarounds.

### New Configuration and Environment Variables
No new environment variables are explicitly introduced in this PR. However, the PR adds a new documentation file (`docs/MEMORY_OPTIMIZATION.md`) that contains:

- JSON configuration examples for memory optimization settings.
- Configurable thresholds for progressive context cleanup.
- Memory usage monitoring parameters and automatic pruning options.

### Installation and Usage Instructions
1. Merge PR #5 into your main branch to apply the v1.0.72 hotfix.
2. Review the newly added `docs/MEMORY_OPTIMIZATION.md` for detailed configuration options.
3. Adjust memory thresholds and cleanup settings according to your environment and workload.
4. Monitor memory usage after deployment to verify the optimizations take effect.

> **Note**: Both issues addressed by this PR lead to **memory exhaustion** and require immediate resolution for stable operation.
