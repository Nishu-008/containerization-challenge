**Challenge - Containerization**
# ***Phase 1***
# Error Log
## Local dev (Exploratory)
### 1. npm warnings regd package installation
  - **Layer:** Backend
  - **Log:** 
  npm warn install-scripts 4 packages had install scripts blocked because they are not covered by allowScripts:
  npm warn install-scripts   @prisma/client@6.0.1 (postinstall: node scripts/postinstall.js)
  npm warn install-scripts   @prisma/engines@6.0.1 (postinstall: node scripts/postinstall.js) 
  npm warn install-scripts   bcrypt@5.1.1 (install: node-pre-gyp install --fallback-to-build)
  npm warn install-scripts   prisma@6.0.1 (preinstall: node scripts/preinstall-entry.js)
  - **Fix:** added packages to allowedScripts in /backend/package.json

### 2. npm audit vulnerabilities
  - **Layer:** Backend
  - **Log1:** 
  17 vulnerabilities (2 low, 2 moderate, 11 high, 2 critical)
  - **Fix1:** ran npm fix and force fix in terminal
  'bash' npm audit fix --force
         
  - **Log2:** 
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
  - **Fix2:** written override commands in .../backend/package.json

  - **Log3:**  
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
 - **Fix:** vulnerabilities ignorable since the packages do not affect production runtime security, verified by  running 
  'bash' npm install --production

### 3. npm warnings regd package installation
  - **Layer:** Frontend
  - **Log:** 
  npm warn install-scripts 1 package had install scripts blocked because they are not covered by allowScripts:
  npm warn install-scripts   esbuild@0.24.0 (postinstall: node install.js)
  - **Fix:** added packages to allowedScripts in /frontend/package.json 
 
### 4. npm audit vulnerabilities
 - **Layer:** frontend
 - **Log1:** 
  36 vulnerabilities (5 low, 7 moderate, 23 high, 1 critical) 
 - **Fix1:** ran npm force fix in terminal
  'bash' npm audit fix --force
 - **Log2:**
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
 - **Fix2:** ran npm force fix again in terminal, since this is not a severe breaking change and involves package upgrade
 found no vulneribilities after force fix

### 5. error due to tailwindcss upgrade by force fix v3 -> v4


 - **Log1:** 
  [vite] Internal server error: [postcss] It looks like you're trying to use `tailwindcss` directly as a PostCSS plugin. The PostCSS plugin has moved to a separate package, so to continue using Tailwind CSS with PostCSS you'll need to install `@tailwindcss/postcss` and update your PostCSS configuration.
  Plugin: vite:css
 - **Fix1:** install new postcss plugin
  'bash' npm install @tailwindcss/postcss tailwindcss

 - **Log2:** 
 [vite] Internal server error: [postcss] tailwindcss: C:/Users/kakku/containerization-challenge/systems-containerization-task-2026/frontend/src/index.css:1:1: Cannot apply unknown utility class `px-6`. Are you using CSS modules or similar and missing `@reference`? https://tailwindcss.com/docs/functions-and-directives#reference-directive
 - **Fix2:** changes in ./frontend/src/index.css
### 6. Log: Uncaught Error: supabaseUrl isrequired  
 -  Fix: I didn't know about supabase. So I set up supabase db. *PS: Later I realized it wasn't even required for what was expected LOL!*

### 7. Log: Post https://dev-evmekbfsg6midmbg.us.auth0.com/oauth/token in network with error code 401. (From console)
  **Fix:** Turns out I was using Auth0 API in wrong way. I had created Application in API Client, which was not the actual way. So I created separate SPA and API, and then supplied

## Local Production (via docker)

### 1. 
- **Layer:** db and backend
- **Log1:** 
Database connection attempt 1 failed: PrismaClientInitializationError: Can't reach database server at `db.oepbjsfggtmcbhqxwxwh.supabase.co:5432` Details: Error loading shared library libssl.so.1.1: No such file or directory (needed by /app/node_modules/.prisma/client/libquery_engine-linux-musl.so.node)

- **Fix:**  changed from node:20-alpine to node:20
 Unlike Alpine Linux variants (node:20-alpine) which use musl libc and frequently cause binary mismatch errors or missing OpenSSL dependencies with Prisma query engines, the standard Debian-based image provides native compatibility out-of-the-box. (AI)

### 2. 
- **Layer:** db and backend
- **Log:** from docker
database

2026-10-20 14:22:28.610 UTC [62] ERROR:  relation "public.Event" does not exist at character 401

2026-10-20 14:22:28.610 UTC [62] STATEMENT:  SELECT "public"."Event"."id", "public"."Event"."name", "public"."Event"."type"::text, "public"."Event"."tagline", "public"."Event"."about", "public"."Event"."maxParticipants", "public"."Event"."minTeamSize", "public"."Event"."maxTeamSize", "public"."Event"."mode"::text, "public"."Event"."status"::text, "public"."Event"."createdAt", "public"."Event"."updatedAt", "public"."Event"."createdById" FROM "public"."Event" WHERE 1=1 ORDER BY "public"."Event"."createdAt" DESC OFFSET $1
backend 

prisma:error 

Invalid `prisma.user.findFirst()` invocation:



The table `public.User` does not exist in the current database.

Registration error: PrismaClientKnownRequestError: 

Invalid `prisma.user.findFirst()` invocation:



The table `public.User` does not exist in the current database.

    at Mn.handleRequestError (/app/node_modules/@prisma/client/runtime/library.js:121:7338)

    at Mn.handleAndLogRequestError (/app/node_modules/@prisma/client/runtime/library.js:121:6663)

    at Mn.request (/app/node_modules/@prisma/client/runtime/library.js:121:6370)

    at async l (/app/node_modules/@prisma/client/runtime/library.js:130:9633)

    at async register (file:///app/src/controllers/auth.js:12:16) {

  code: 'P2021',

  clientVersion: '6.0.1',

  meta: { modelName: 'User', table: 'public.User' }

}
 **Fix:** added migrate deploy in ./backend/DockerFile line 13 

### 3. env var update
 ![Screenshot](/systems-containerization-task-2026/imgs/errimg1.png)
 - The first error (Access to XHTMLRequest...) was due to old CORS var (http://localhost:3000). This time the rev proxy listens at http://localhost:80 or simply http://localhost
 - **Fix:** updated CORS_ORIGIN in /backend/.env
  All the subsequent errors are fixed by this change. (API,Axios: Network and POST errors)

# ***Phase 2***
 The resulting image size of frontend Dockerfile is 1.86 GB(!!)
![Before](/imgs/before.png)
 It is required to reduce it to under 110 MB

 node:20 pulls a full-debian based image.
 npm install includes heavy build dependencies.
 This means final container is carrying around every single development dependency, the entire node_modules folder, and the Node.js runtime environment itself—just to run a lightweight static file server (npx serve).

 We don't need all whole architecture. In production, frontend only has pure static files. Whole node.js is not required just to serve static files, Since the code is already built.
![After](/imgs/after.png)
 Genuinely I used AI to generate a Dockerfile. But I am genuinely tried to understand what's actually happening.

# How I reproduced the stack: (forgot to write it in the beginning)
  - I went through README.md and understood the app architecture.
  - I started with local dev. I don't know why. Maybe I was curious. But it was unhinged from the main challenge(sorry!)
  - I, in co-ordination with AI, (wasted time in local dev)
  - test ran given docker compose.
  - struggled with compatibility issues in backend node-alpine (musl vs gblic). Finally I went with node ( yeah it increased it's size to 1.82 gb which I observed in phase 2.) 
  - Then I got caught up in Auth0 integration(which was not required too).
# Experience (wasn't asked, but I wanted to write this)
I think I got carried away by small stuff yet I have learned a lot of new things. I am way unprofessional in this stuff. But I aim towards professionalism. (should've saved it for interview).

# Conclusion
 I was not able to go to further phases. I have used AI extensively. I'm a newbie to this area: FSD, Containerization and all stuff.
 But I think I am enthusiastic enough. Hope I'll project it well enough too.
 Apologies if I have not followed some code for write-up and all.

 *Nishanth Kakkuppi (Nishu-008) : 261DS018*