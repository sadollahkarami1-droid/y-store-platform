# Y Store AI — Performance Constitution

Performance is a release requirement, not a later optimization task.

## Mobile targets
- Release/profile builds are the source of performance truth; debug performance is not accepted as a benchmark.
- Target 60 fps on supported mainstream devices; 120 fps where hardware permits.
- Avoid avoidable frame work above ~16 ms at 60 Hz.
- Navigation must not wait for unrelated API calls.
- Use lazy list/grid builders for large product collections.
- Paginate or cursor-load every unbounded collection.
- Cache shell/navigation state and recently visited screens.
- Preload only high-probability next-screen data; never preload the full catalog.
- Decode appropriately sized images, use thumbnails and modern compressed formats.
- Keep heavy parsing, transforms and AI work off the UI thread.
- Preserve screen state where appropriate to prevent wasteful refetch/rebuild cycles.

## Web targets
- Customer storefront is server-rendered/streamed where useful for fast first content and SEO.
- Send minimal client JavaScript for catalog/browse pages.
- Image CDN + responsive image sizing.
- Route-level and component-level streaming/skeleton states.
- Edge/CDN caching for public catalog data where policy permits.

## Backend targets
- No N+1 database access in critical catalog/cart/checkout paths.
- Index query patterns, not merely columns.
- Cursor pagination for high-volume tables.
- Redis caching only where invalidation is explicit and measurable.
- All payment/order mutation endpoints require idempotency strategy.
- Slow external calls are isolated with timeouts, retries and circuit-breaking policy.
- Long-running jobs run asynchronously through workers/queues.

## Performance gates
Each release tracks:
- app cold-start and warm-start
- time to first usable screen
- screen transition latency
- API p50/p95/p99 latency
- dropped/janky frames
- memory usage
- binary size
- image/network payload size
- database slow-query count

A feature that violates the agreed budget is not considered complete.
