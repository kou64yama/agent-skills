---
name: merge-pull-request
description: Check repository merge requirements and merge an authorized GitHub pull request.
---

# Merge a Pull Request

Identify the repository and PR. Retrieve contribution guidelines through the target repository's GitHub API, preferring GraphQL `contributingGuidelines` over local files, and use what the API returns without separately resolving inherited defaults. Consider applicable repository instructions and report sources that cannot be checked. Check the PR's current state, target, required reviews and checks, mergeability, and available merge methods against the repository's rules. Resolve the merge method from the user's instruction or repository convention; ask if a consequential choice remains ambiguous.

Merge only when requested and requirements are satisfied. Record the head SHA assessed during the checks and supply it as a merge precondition. If the head no longer matches, reassess the PR before attempting a merge again. Use a merge operation that supports this precondition; if none is available, report the blocker rather than merging without it. If blocked, explain the specific blocker; do not bypass protections or change repository settings. Verify and report the resulting PR state. Advice or a readiness check alone does not authorize a merge.
