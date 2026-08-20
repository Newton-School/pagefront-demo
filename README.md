# pagefront-demo

Throwaway pilot for **pagefront** (NS-13606). A minimal static site — one HTML
page plus a content-hashed JS and CSS — used to verify the edge fronting.

Requirements it satisfies as a pagefront origin: GitHub **Pages enabled**, **no
custom domain** (so `newton-school.github.io/pagefront-demo/` serves directly).

Fronted at `https://pagefront-demo-pages.newtonschool.co/` once the DNS record
(proxied `CNAME … → newton-school.github.io`) and the `*-pages.newtonschool.co/*`
Worker route exist.

Expected headers via pagefront:
- `/` → `Cache-Control: no-cache`
- `/assets/app-A1b2C3d4.js`, `/assets/style-X9y8Z7w6.css` → `public, max-age=86400, immutable`
- `x-pagefront-cache: HIT` on a repeat load
