# SEMOSS Knowledge

## Purpose
Provide a base overview of the SEMOSS platform directory structure so agents know where to look when working on SEMOSS-related tasks.

## Platform Overview

SEMOSS is a full-stack analytics and AI platform. The workspace contains three main codebases:

### Frontend — `portals/` (SemossWeb)
- The built/deployed UI assets served by Tomcat under the `/SemossWeb` path.
- `portals/` contains the compiled production build (`index.html`, `assets/`).
- Source code for the UI lives in a separate `semoss-ui` repo (not always present in this workspace). When it is present, look for a top-level `semoss-ui/` or similar directory.

### Backend Core — `Semoss/`
- The core SEMOSS Java engine. Package root: `src/prerna/`.
- Key packages:
  - `reactor/` — Pixel reactors (the command/query execution layer).
  - `engine/` — Database, model, storage, and vector engine interfaces.
  - `auth/` & `security/` — Authentication utilities and security/OWL schema management.
  - `query/` — Query parsing and interpreters.
  - `ds/` — DataSet / frame abstractions.
  - `project/` — Project-level logic.
  - `util/` — Shared utilities.
  - `cluster/` — Cluster / multi-node coordination.
- Config files: `config/`, `social.properties`, `RDF_Map.prop`.
- Python helpers: `py/`.
- Build: Maven (`pom.xml`).

### Web Layer — `Monolith/`
- The Java web application (WAR) that wraps Semoss and exposes REST APIs via Tomcat.
- Package root: `src/prerna/`.
  - `web/` — JAX-RS REST endpoints (the `/api/` routes).
  - `auth/` — Login providers, SAML, session management.
  - `semoss/` — Servlet and application lifecycle.
  - `upload/` — File upload handling.
  - `cluster/` — Cluster-specific web endpoints.
  - `mcp/` — Model Context Protocol integration.
  - `websocket/` — WebSocket endpoints.
- `WebContent/` — Static web resources, login pages, SAML config.
- Build: Maven (`pom.xml`) + Ant (`build.xml`).

### Other Workspace Directories
- `apache-tomcat-9.0.113/` — Local Tomcat server used to run Monolith + SemossWeb.
- `h2/` — H2 database files (local metadata/security DBs).
- `models/` — Local model artifacts.
- `docker-r-python/` — Docker setup for R/Python runtimes.
- `Servers/` — Server configuration.

## Quick Reference

| What you need | Where to look |
|---|---|
| REST API endpoints | `Monolith/src/prerna/web/` |
| Pixel reactor logic | `Semoss/src/prerna/reactor/` |
| Engine interfaces (DB, model, vector, storage) | `Semoss/src/prerna/engine/` |
| Security / OWL schema | `Semoss/src/prerna/security/`, `Semoss/src/prerna/auth/` |
| Login / auth providers | `Monolith/src/prerna/auth/` |
| Frontend UI build | `portals/` |
| Tomcat deployment | `apache-tomcat-9.0.113/` |
| Token / model configuration | `Semoss/src/prerna/reactor/` + `Monolith/src/prerna/web/` |
