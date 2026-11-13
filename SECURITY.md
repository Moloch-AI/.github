# Security policy

This policy covers every repository in the Moloch-AI organization, unless a repository has its own `SECURITY.md`.

## Reporting a vulnerability in these repositories

Please report vulnerabilities privately. Do not open a public issue, discussion or pull request.

1. Open the affected repository on GitHub.
2. Go to the **Security** tab and choose **Report a vulnerability**.
3. Describe the issue, the affected version or commit, how to reproduce it, and the impact you expect.

We will acknowledge the report, keep you updated while we work on a fix, and credit you in the release notes if you would like to be credited.

## Reporting a problem with the hosted API or dashboard

Security issues in the MolochAI service itself (`api.molochai.dev`, `dash.molochai.dev`, `molochai.dev`) are not in these repositories. Report them through [molochai.dev/contact](https://molochai.dev/contact).

## If an API key leaks

Revoke it right away in the [dashboard](https://dash.molochai.dev/account) under **API keys**, then create a new one. Revoking takes effect immediately. A MolochAI key is not scoped: whoever holds it can spend your quota and read your account details through the API. Never include a key in an issue, a log excerpt, a screenshot or a report, including a private one.

## Supported versions

Fixes are made on the default branch and released in the next version of the affected repository. Older releases are not patched separately.
