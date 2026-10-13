<!-- markdownlint-disable -->

# Hardening Report: ruzickap--action-my-markdown-link-checker/v1.5.2

> This file was generated automatically by the hardening agent.

**Policy SHA:** `d636be7e43ef829af6e853da6b3c7566db9f72fe`

**Test Policy SHA:** `843adf9e4b8f85d0c08b27b9d0b09dd094b54702`

**Harden Agent Version:** `2`

Action **ruzickap--action-my-markdown-link-checker/v1.5.2** was hardened automatically. 0 finding(s) were identified and resolved across 1 iteration(s).

## Iteration Notes

### Iteration 1

**Fixes applied:** script-injection

**Notes:**

Fixed script injection vulnerability in entrypoint.sh at line 63. The unquoted expansions of ${FD_CMD_PARAMS} and ${SEARCH_PATHS} in the `fd` command were replaced with properly tokenized bash arrays. Each variable is now tokenized using the xargs null-delimited read loop pattern (with required if [ -n ... ] guards), and expanded safely as "${ARRAY[@]}". The `# shellcheck disable=SC2086` comment was removed. The script uses bash (confirmed by #!/usr/bin/env bash shebang and Dockerfile installing bash), so array syntax and process substitution are safe to use.

