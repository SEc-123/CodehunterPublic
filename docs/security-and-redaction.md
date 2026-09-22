# Security and redaction rules for public documentation

The public repository is safe to clone and share. Do not commit any of the following:

- API keys, bearer tokens, SSH private keys, passwords, cookies, license keys, activation codes, enrollment codes, or signed capability tokens.
- Real customer email addresses, production workspace identifiers, private repository URLs, internal hostnames, internal IP addresses, or provider endpoints that are not public.
- Local absolute paths such as `/absolute/local/path`, home directories, SQLite files, Electron user-data directories, or raw production logs.
- Screenshots that expose secrets in a form field, browser address bar, terminal, notification, or clipboard preview.
- Real customer source code, production reports, vulnerability details that are not approved for disclosure, or generated files containing embedded credentials.

## Safe capture procedure

1. Use separate Personal and Team `CODE_HUNTER_HOME` and Electron user-data directories.
2. Use a neutral demo project such as `CodeHunter Demo App`.
3. Enter `••••••••` or an obviously fake placeholder in provider screenshots; never type a real secret and blur only after capture.
4. Use fake workspace members and a local fixture SCM source.
5. Inspect the image and extracted OCR/text before copying it into the public repository.
6. Record source commit, edition, step id, capture method, SHA-256, and redaction status in `docs/assets/manifest-3.1.94.json`.

If a screenshot or package cannot pass these checks, remove it from the public candidate and keep it in private validation storage only.
