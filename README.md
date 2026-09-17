# Y Store AI

Universal multi-tenant commerce platform for sales, rental, booking, services, B2B/B2C/C2C, marketplaces, white-label storefronts and AI-assisted commerce.

## Status
Phase 0 — Foundation and architecture.

## Non-negotiable architecture principles
- Multi-tenant, multi-store, multi-vendor, multi-country, multi-language, multi-currency
- Sales + rental + booking + services from the same commerce core
- API-first, event-driven, modular architecture
- Configuration-driven vertical packs; no business/industry logic hard-coded into the core
- AI-native, but AI never bypasses permissions, policy, audit or financial controls
- Performance-first: lazy loading, pagination, cache, image optimization, background work and strict performance budgets
- Security, auditability, backups, migrations and rollback from day one

## Planned applications
- Customer mobile app
- Seller mobile app
- Business/B2B app
- Creator app
- Delivery app
- POS
- Customer web storefront
- Seller/Admin web consoles

## Planned core domains
Identity, Tenant, Organization, Store, Catalog, Marketplace, Offer, Pricing, Inventory, Rental Assets, Availability, Cart, Checkout, Order, Payment, Ledger, Logistics, Returns, Trust, Reviews, Search, Recommendations, Social Commerce, Live Commerce, Creator/Affiliate, Ads, Analytics and AI.

## Repository strategy
Monorepo during the foundation and early product stages, with strict domain boundaries so services can later be extracted without rewriting the business core.
