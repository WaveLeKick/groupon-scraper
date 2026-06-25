[Groupon Scraper](https://apify.com/santamaria-automations/groupon-scraper?fpr=data)

# Groupon Deal Scraper — International

Scrapes deals from Groupon across **12 countries**: DE, US, UK, FR, IT, ES, NL, BE, AT, PL, AU, IE.

## How it works

1. Loads Groupon browse pages which contain `__NEXT_DATA__` with the full Apollo GraphQL cache
2. Extracts deal cards (9 per page) from the SSR data — no browser needed
3. **Category fan-out**: Discovers category sub-pages and loads each one to collect ~80 unique deals per city
4. Deduplicates by UUID across categories
5. Optionally fetches detail pages for full descriptions, options, locations, and reviews

## Use with AI Agents (MCP)

Connect this actor to any MCP-compatible AI client — Claude Desktop, Claude.ai, Cursor, VS Code, LangChain, LlamaIndex, or custom agents.

**Apify MCP server URL:**

```
https://mcp.apify.com?tools=santamaria-automations/groupon-scraper
```

**Example prompt once connected:**

> "Use `groupon-scraper` to scrape company data from groupon. Return results as a table."

Clients that support dynamic tool discovery (Claude.ai, VS Code) will receive the full input schema automatically via `add-actor`.

## Input

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `country` | enum | `DE` | Country code (DE, US, UK, FR, IT, ES, NL, BE, AT, PL, AU, IE) |
| `city` | string | `berlin` | City name for URL path |
| `category` | string | `""` | Optional category slug filter |
| `query` | string | `""` | Optional search keyword (overrides browse) |
| `maxResults` | integer | `100` | Max deals to return |
| `includeDetails` | boolean | `false` | Fetch detail pages for full data |
| `proxyConfiguration` | object | Apify proxy | Proxy settings |

## Output fields

### SERP (always available)

`title`, `deal_url`, `deal_id`, `deal_slug`, `merchant_name`, `merchant_rating`, `merchant_rating_count`, `price`, `original_price`, `currency`, `discount_percent`, `location_name`, `location_address`, `latitude`, `longitude`, `locations_total`, `image_url`, `category`

### Detail (with `includeDetails: true`)

`description`, `highlights`, `fine_print`, `sold_quantity`, `expiry_date`, `merchant_website`, `merchant_phone`, `merchant_address`, `opening_hours`, `review_rating`, `review_count`, `options[]`, `locations[]`

## Performance

- **HTTP-only** — CheerioCrawler, ~128MB RAM
- **~80 deals per city** via category fan-out (no API calls needed)
- Datacenter proxy works fine

## Enrichment add-ons

After the scrape completes, this actor can automatically trigger AI-powered extraction on every merchant website found in the results. Each add-on runs as a separate actor and produces its own dataset.

### Contact extraction

Extracts team member names, email addresses, phone numbers, positions, and departments from merchant websites. Powered by the [Website Contact Extractor](https://apify.com/santamaria-automations/website-contact-extractor).

Enable it by setting `enableContactExtraction: true` and providing at least one LLM API key. The sub-actor run ID is stored in the key-value store as `CONTACT_EXTRACTOR_RUN_ID`.

### Job listing extraction

Extracts open positions, job titles, locations, departments, and career page URLs from merchant websites. Powered by the [Website Job Extractor](https://apify.com/santamaria-automations/website-job-extractor).

Enable it by setting `enableJobExtraction: true` and providing at least one LLM API key. The sub-actor run ID is stored in the key-value store as `JOB_EXTRACTOR_RUN_ID`.

### Browser fallback

Some websites are built with JavaScript frameworks (React, Vue, Angular) that require a full browser to render. When `enableBrowserFallback` is set to `true`, the contact/job extractors will automatically re-scrape these sites with Playwright. This catches ~25% more sites but increases cost and runtime. Only applies when contact or job extraction is enabled.

### LLM API keys

Both add-ons use LLMs to extract structured data. Provide one or more API keys. When multiple keys are provided, the system uses them in priority order with automatic fallback:

1. **Gemini** (recommended) -- Best quality-to-cost ratio. Free tier includes 1M tokens/min. Get a key at [Google AI Studio](https://aistudio.google.com/app/apikey).
2. **Groq** (optional) -- Ultra-fast inference. Get a key at [Groq Console](https://console.groq.com/keys).
3. **OpenRouter** (optional) -- Access to 100+ models. Get a key at [OpenRouter](https://openrouter.ai/keys).

One key is sufficient. With multiple keys, if the primary provider hits a rate limit, the system falls back to the next available provider automatically.

## Related Actors

**E-Commerce & Price Comparison**

- [AutoScout24 Scraper — European car listings](https://apify.com/santamaria-automations/autoscout24-scraper)
- [AliExpress Scraper — Global marketplace](https://apify.com/santamaria-automations/aliexpress-scraper)
- [Galaxus.ch Scraper — Swiss electronics retailer](https://apify.com/santamaria-automations/galaxus-ch-scraper)
- [Booking.com Scraper — Hotel listings](https://apify.com/santamaria-automations/booking-com-scraper)

**Classifieds**

- [Kleinanzeigen.de Scraper — Germany](https://apify.com/santamaria-automations/kleinanzeigen-de-scraper)
- [Willhaben.at Scraper — Austria](https://apify.com/santamaria-automations/willhaben-at-scraper)
- [Marktplaats.nl Scraper — Netherlands](https://apify.com/santamaria-automations/marktplaats-nl-scraper)

**Enrich your data**

- [Website Email & Phone Scraper](https://apify.com/santamaria-automations/website-email-scraper)
- [Google Maps Scraper](https://apify.com/santamaria-automations/google-maps-scraper)
- [Website Contact Extractor](https://apify.com/santamaria-automations/website-contact-extractor)

## Support

Found a bug or have a feature request? [Open an issue](https://console.apify.com/actors/pj5yPSeJ0AyNzXjfj/issues).