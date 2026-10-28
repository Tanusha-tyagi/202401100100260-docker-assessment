# FestPass container security assessment

## Assessment details

- Name: **Tanusha Tyagi**
- REGNO: **202401100100260**
- PORT: **140**
- Docker Hub username: **tanushatyagi**
- Docker Hub repository: **https://hub.docker.com/r/tanushatyagi/fest-backend**
- AI tools: **Copilot in VS Code** — used to review the assessment, update container configuration and dependencies, and run checks.

## Vulnerability scan results

| Image | CRITICAL | HIGH | Image size |
|---|---:|---:|---:|
| `fest-backend:0.1` (before) | 234 | 2,249 | 1.61 GB |
| `fest-backend:0.2` (after) | 0 | 49 | 218 MB |

Counts are summed across the OS and Python package targets in the Trivy reports.
The CRITICAL-with-fix gate for `fest-backend:0.2` exited with code 0. The image
still has HIGH and other findings; this is not a clean overall scan.
Reports: `reports/trivy-before.txt` and `reports/trivy-after.txt`.

## Release status

- Docker Hub tags `1.0.0` and `1.0` were pushed with digest
  `sha256:b833fc00923bebba8e4e6ab80e41fac2584f7bd8b6abcd09681dae5a8c40a74e`.
- Compose uses `tanushatyagi/fest-backend:1.0.0`; its registry pull and health
  endpoint were verified on port 140 with the existing registrations intact.
- Stage 5 signing and unsigned-release rejection are pending at this point in
  the commit history.

## Incomplete steps

- Capture the required unedited terminal and browser evidence in `screenshots/`.
