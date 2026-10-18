# Axiom browser playground release

This folder is a runnable, static presentation of the experimental finite v1
Axiom language. Serve it over HTTP/HTTPS; opening index.html as file:// does not
support Workers. For a local preview: `python -m http.server 8765 --directory PATH`.
The browser runs the real Python compiler, checked plan interpreter, and original
source evaluator in a Web Worker. No compilation server or account is needed.

## Scope and publication

Publishing this folder discloses the source of the eleven modules listed in
release-manifest.json. The ZIP is source code, not a secrecy mechanism. This
artifact excludes Core, scalable research, receipts, recovery material, session
logs and Git history. Review these exact bytes before any public upload.
The bounded demo is released under the MIT License in LICENSE, copyright 2026
NtEuphoria. This grant covers the eleven compiler/runtime Python modules named
in release-manifest.json, the five UI/transport assets (index.html, app.js,
style.css, transport.js, worker.js), and their accompanying demo documentation.
It does not grant a license to excluded Axiom research, recovery records, Core,
or any other private repository material. Third-party runtime files retain their
own licenses described below. The build command itself does not deploy, create
a public repository, or register a Stardance submission.

The supported profile is one exact i32 two-stage stencil, with
(H+1)*(W+1) <= 256 and input values 0..1023. Reports are independently compared
observations, not native performance measurements, scalable proof certificates,
or O3 qualification receipts. The user can inspect and modify browser code;
therefore a downloaded report is not an authoritative attestation.

## Runtime and network

Pyodide 0.27.7, Python 3.12.7. Runtime mode: **vendor**.
The runtime is vendored and hash-checked. The application fetches only files from its own origin, about 14 MB on first load; normal browser caching applies.
No Python packages beyond the bundled standard library are loaded. Source and
input values stay in the browser. There is no analytics or project submission.
Initialization has a 60-second timeout; computations have a 15-second timeout.
A timeout terminates the Worker and the next request starts a fresh runtime.

Pyodide source and MPL-2.0 license:
https://github.com/pyodide/pyodide/tree/0.27.7
Python source and license:
https://github.com/python/cpython/tree/v3.12.7
The vendor build includes their license texts under runtime/.

## Hosting

Upload this folder as static files only after publication approval. Relative
asset paths support a site root or a repository subpath. Serve .js as JavaScript,
.wasm as application/wasm, and .json as application/json. No SPA rewrite or
backend function is needed. HTTPS is recommended for public hosting.

The _headers file configures compatible hosts (such as Cloudflare Pages or
Netlify). Other hosts must configure equivalent headers separately. GitHub
Pages ignores _headers; the document also carries a CSP meta tag. A Worker needs
script-src 'self' 'wasm-unsafe-eval', connect-src 'self', and worker-src 'self'.
For CDN mode also allow https://cdn.jsdelivr.net in script-src and connect-src.
Do not add unsafe-eval, broad wildcard origins, or disable TLS to fix startup.

release-manifest.json lists every release file's size and SHA-256, excluding
itself to avoid a recursive hash. Its compiler_modules field lists the eleven
Python sources; compiler_archive_members additionally records the LICENSE
carried inside axiom-compiler.zip for standalone downloads. Rebuilds are
deterministic for identical inputs.
