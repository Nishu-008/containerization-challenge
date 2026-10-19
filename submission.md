# Error Log
- 1. npm warnings regd package installation
  **Layer:** Backend
  **Log:** 
  npm warn install-scripts 4 packages had install scripts blocked because they are not covered by allowScripts:
  npm warn install-scripts   @prisma/client@6.0.1 (postinstall: node scripts/postinstall.js)
  npm warn install-scripts   @prisma/engines@6.0.1 (postinstall: node scripts/postinstall.js) 
  npm warn install-scripts   bcrypt@5.1.1 (install: node-pre-gyp install --fallback-to-build)
  npm warn install-scripts   prisma@6.0.1 (preinstall: node scripts/preinstall-entry.js)
  **Fix:** added packages to allowedScripts in /backend/package.json

- 2. npm audit vulnerabilities
  **Layer:** Backend
  **Log1:** 
  17 vulnerabilities (2 low, 2 moderate, 11 high, 2 critical)
  **Fix1:** ran npm fix and force fix in terminal
  'bash' npm audit fix --force
         
  **Log2:** 
   braces  *
  Severity: high
  braces vulnerable to stack-exhaustion denial of service through deeply nested patterns - https://github.com/advisories/GHSA-vfj7-8cjw-p6xm
  fix available via `npm audit fix --force`
  Will install nodemon@1.14.10, which is a breaking change
  node_modules/braces
  chokidar  2.0.0 - 3.6.0
  Depends on vulnerable versions of braces
  node_modules/chokidar
    nodemon  0.0.0-development || >=1.14.11
    Depends on vulnerable versions of chokidar
    node_modules/nodemon

  tar  <=7.5.20
  Severity: critical
  node-tar Vulnerable to Arbitrary File Creation/Overwrite via Hardlink Path Traversal - https://github.com/advisories/GHSA-34x7-hfp2-rc4v
  node-tar is Vulnerable to Arbitrary File Overwrite and Symlink Poisoning via Insufficient Path Sanitization - https://github.com/advisories/GHSA-8qq5-rm4j-mr97
  Arbitrary File Read/Write via Hardlink Target Escape Through Symlink Chain in node-tar Extraction - https://github.com/advisories/GHSA-83g3-92jg-28cx
  tar has Hardlink Path Traversal via Drive-Relative Linkpath - https://github.com/advisories/GHSA-qffp-2rhf-9h96
  node-tar Symlink Path Traversal via Drive-Relative Linkpath - https://github.com/advisories/GHSA-9ppj-qmqm-q256
  Race Condition in node-tar Path Reservations via Unicode Ligature Collisions on macOS APFS - https://github.com/advisories/GHSA-r6q2-hw4h-h46w
  node-tar applies PAX size override to intermediary GNU long-name/long-link headers, causing tar parser interpretation differential (file smuggling) - https://github.com/advisories/GHSA-vmf3-w455-68vh
  node-tar: Process crash via PAX numeric path type confusion - https://github.com/advisories/GHSA-w8wr-v893-vjvp
  node-tar: Decompression/parse DoS via unlimited input - https://github.com/advisories/GHSA-23hp-3jrh-7fpw
  node-tar: Negative tar entry size causes infinite loop in archive replace - https://github.com/advisories/GHSA-8x88-c5mf-7j5w
  node-tar: Uncaught Exception DoS via NUL byte in PAX path/linkpath records - https://github.com/advisories/GHSA-gvwx-54wh-qm9j
  node-tar: Uncontrolled recursion in mapHas/filesFilter allows uncatchable stack-overflow DoS via crafted long-path tar with member selection - https://github.com/advisories/GHSA-r292-9mhp-454m
  fix available via `npm audit fix`
  node_modules/tar
  @mapbox/node-pre-gyp  <=1.0.11
  Depends on vulnerable versions of tar
  node_modules/@mapbox/node-pre-gyp
  5 vulnerabilities (4 high, 1 critical)
  **Fix2:** written override commands in .../backend/package.json
  **Log3:**  
  braces  *
  Severity: high
  braces vulnerable to stack-exhaustion denial of service through deeply nested patterns - https://github.com/advisories/GHSA-vfj7-8cjw-p6xm
  fix available via `npm audit fix --force`
  Will install nodemon@1.14.10, which is a breaking change
  node_modules/braces
  chokidar  2.0.0 - 3.6.0
  Depends on vulnerable versions of braces
  node_modules/chokidar
    nodemon  0.0.0-development || >=1.14.11
    Depends on vulnerable versions of chokidar
    node_modules/nodemon

  3 high severity vulnerabilities
 **Fix:** vulnerabilities ignorable since the packages do not affect production runtime security, verified by  running 
  'bash' npm install --production

- 3. npm warnings regd package installation
  **Layer:** Frontend
  **Log:** 
  npm warn install-scripts 1 package had install scripts blocked because they are not covered by allowScripts:
  npm warn install-scripts   esbuild@0.24.0 (postinstall: node install.js)
  **Fix:** added packages to allowedScripts in /frontend/package.json 
 
- 4. npm audit vulnerabilities
 **Layer:** frontend
 **Log1:** 
  36 vulnerabilities (5 low, 7 moderate, 23 high, 1 critical) 
 **Fix1:** ran npm force fix in terminal
  'bash' npm audit fix --force
 **Log2:**
  npm audit report

  react-router  6.0.0 - 7.17.0
  Severity: moderate
  React Router: Open redirect via backslash in <Link> and useNavigate (CVE-2025-68470 bypass) - https://github.com/advisories/GHSA-wrjc-x8rr-h8h6
  React Router: Arbitrary Constructor Injection via deserializeErrors() in React Router SSR Hydration - https://github.com/advisories/GHSA-337j-9hxr-rhxg
  fix available via `npm audit fix --force`
  Will install react-router-dom@7.18.4, which is a breaking change
  node_modules/react-router
  react-router-dom  6.0.0-alpha.0 - 7.17.0
  Depends on vulnerable versions of react-router
  node_modules/react-router-dom

  2 moderate severity vulnerabilities
 **Fix2:** ran npm force fix again in terminal, since this is not a severe breaking change and involves package upgrade
 found no vulneribilities after force fix

- 5. error due to tailwindcss upgrade by force fix v3 -> v4


 **Log1:** 
  [vite] Internal server error: [postcss] It looks like you're trying to use `tailwindcss` directly as a PostCSS plugin. The PostCSS plugin has moved to a separate package, so to continue using Tailwind CSS with PostCSS you'll need to install `@tailwindcss/postcss` and update your PostCSS configuration.
  Plugin: vite:css
 **Fix1:** install new postcss plugin
  'bash' npm install @tailwindcss/postcss tailwindcss

 **Log2:** 
 [vite] Internal server error: [postcss] tailwindcss: C:/Users/kakku/containerization-challenge/systems-containerization-task-2026/frontend/src/index.css:1:1: Cannot apply unknown utility class `px-6`. Are you using CSS modules or similar and missing `@reference`? https://tailwindcss.com/docs/functions-and-directives#reference-directive
 **Fix2:** changes in ./frontend/src/index.css
  
