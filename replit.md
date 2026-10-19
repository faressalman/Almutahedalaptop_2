# المتحدة لابتوب

واجهة عربية متجاوبة لاستكشاف أجهزة لابتوب مستعملة ومجددة وتجربة التصفح والسلة ونموذج الحجز محلياً.

## Run & Operate

- `pnpm --filter @workspace/almutaheda-laptop run dev` — run the storefront preview
- `pnpm --filter @workspace/almutaheda-laptop run typecheck` — check the storefront TypeScript
- `pnpm --filter @workspace/almutaheda-laptop run build` — build the storefront
- `pnpm run typecheck` — full typecheck across all packages
- `pnpm run build` — typecheck + build all packages
- `pnpm --filter @workspace/api-spec run codegen` — regenerate API hooks and Zod schemas from the OpenAPI spec
- `pnpm --filter @workspace/db run push` — push DB schema changes (dev only)
- The storefront needs no secrets or database connection in its current demo mode.

## Stack

- pnpm workspaces, Node.js 24, TypeScript 5.9, React, Vite, Tailwind CSS
- Storefront state is client-side; product samples, cart, and theme use browser local storage.
- The workspace also contains an Express API, PostgreSQL/Drizzle library, and OpenAPI code generation scaffold; the storefront does not currently call them.

## Where things live

- `artifacts/almutaheda-laptop/src/App.tsx` — pages and storefront interactions.
- `artifacts/almutaheda-laptop/src/data/products.ts` — sample product records.
- `artifacts/almutaheda-laptop/src/index.css` — storefront styles.
- `artifacts/almutaheda-laptop/public/` — logo, product images, and favicon.
- `artifacts/api-server/` and `lib/db/` — shared backend scaffolding, not used by the current storefront.

## Architecture decisions

- The current app intentionally remains a demo; its products and prices are examples, not live inventory.
- Cart and sample-admin edits are local to each browser. Contact submissions and booking confirmation are not sent or stored.
- Syriatel Cash is shown only as a payment simulation. No payments or transfers occur.
- The `/admin` page is a public demo screen and must not be treated as a secure admin console.

## Product

Users can browse and filter six laptop samples, view product details, save a local cart, calculate a sample 10% deposit, and try a local contact form. The UI is Arabic and RTL, while product/model names remain in English.

## User preferences

- The user chose to keep this artifact as an interactive demo; do not enable real bookings, store real customer data, or connect real payments unless they explicitly request that change.
- Keep the UI Arabic, RTL, and responsive on phones, tablets, and computers.
- Use the existing official store logo.
- Keep laptop names and model names in English.
- Show a 10% deposit and Syriatel Cash only as a demo unless a real payment flow is explicitly configured.
- Do not expose customer records to visitors.
- Explain project progress and next steps in simple Arabic.
- For a real booking, the manager should receive an in-site notification.

## Gotchas

- This release is a storefront demo, not an operational shop: real orders, inventory, customer contact, admin login, persistent shared data, and payment are not implemented.
- Before using it to accept real reservations, add server-side persistence, protect admin access, define the actual inventory and store policies, and implement the agreed manager notification flow.

## Pointers

- See the `pnpm-workspace` skill for workspace structure, TypeScript setup, and package details
- Imported from https://github.com/faressalman/Almutahedalaptop (commit `d743dd7ec9ce7b9330c62a97517c08a874dbcf56`)
