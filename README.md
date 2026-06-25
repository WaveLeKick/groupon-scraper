[Groupon Scraper](https://apify.com/lulzasaur/groupon-scraper?fpr=data)

Scrape local deals and discounts from [Groupon.com](https://www.groupon.com). Extract deal prices, original prices, discount percentages, merchant info, ratings, and more across 500+ cities and 15+ categories.

## Features

- Scrape deals by **city** and **category** (things to do, food & drink, beauty & spas, etc.)
- **Search** for specific deals by keyword
- Extract **prices, discounts, promo codes**, and expiration dates
- Get **merchant ratings** and review counts
- Automatic **multi-category expansion** to fill your result quota
- **Deduplication** built-in

## Input

| Field | Type | Default | Description |
| --- | --- | --- | --- |
| `city` | string | `denver` | City slug (e.g. `chicago`, `new-york`, `los-angeles`) |
| `category` | select | `things-to-do` | Deal category |
| `query` | string | *(empty)* | Search keyword (overrides city/category) |
| `maxResults` | integer | `100` | Maximum deals to return (1-1000) |
| `proxyConfiguration` | object | - | Optional proxy configuration |

### Available Categories

`things-to-do`, `food-and-drink`, `beauty-and-spas`, `health-and-fitness`, `automotive`, `home-services`, `goods`, `museums`, `retail`, `nightlife`, `concerts`, `fun-and-leisure-activities`, `restaurants`, `massage`, `chiropractor`, `laser-hair-removal`

### Popular Cities

`new-york`, `los-angeles`, `chicago`, `houston`, `phoenix`, `philadelphia`, `san-antonio`, `san-diego`, `dallas`, `san-jose`, `austin`, `denver`, `seattle`, `boston`, `nashville`, `miami`, `atlanta`, `portland`, `las-vegas`, `minneapolis`

## Output

Each deal includes:

```
{
    "title": "Two-Hour Trail Ride - National Park Gateway Stables",
    "price": 82,
    "originalPrice": 115,
    "promoPrice": 65.60,
    "discount": 33,
    "discountPercent": 29,
    "promocode": "TOPDEALS",
    "promoExpiresAt": "2026-04-27T06:59:00.000Z",
    "currency": "USD",
    "merchant": "4600 Fall River Road, Estes Park",
    "merchantRating": 4.9,
    "reviewCount": 510,
    "category": "things-to-do",
    "city": "denver",
    "imageUrl": "https://img.grouponcdn.com/deal/.../t700x420.webp",
    "dealUrl": "https://www.groupon.com/deals/national-park-gateway-stables-2",
    "dealId": "4e0f67d6-2d9a-4567-bf03-2ce9664d4bed",
    "isSponsored": false,
    "scrapedAt": "2026-04-25T12:00:00.000Z"
}
```

## How It Works

1. Fetches Groupon category pages via server-side rendered HTML
2. Extracts deal data from embedded JSON in `data-bhd` attributes (Next.js hydration data)
3. If more results are needed, automatically expands to additional categories
4. Deduplicates deals by ID to avoid repeats across categories

## Use Cases

- **Price monitoring** — Track local deal prices over time
- **Market research** — Analyze discount patterns by city/category
- **Deal aggregation** — Build deal comparison tools
- **Business intelligence** — Monitor competitor promotions
- **Travel planning** — Find best deals in destination cities

## Notes

- Groupon serves ~9 deals per category page via SSR
- For larger result sets, the scraper automatically crawls multiple categories
- Search mode returns deals matching your keyword across all categories
- No login required, no anti-bot protection