[Groupon Scraper](https://apify.com/sovereigntaylor/groupon-scraper?fpr=data)

# Groupon Deals & Coupons Scraper

Scrape Groupon deals, coupons, and local offers at scale. Extract deal titles, original and discounted prices, savings percentages, merchant details, star ratings, sold counts, categories, expiration dates, fine print, and images. Export to JSON, CSV, Excel, or connect directly to your app via the Apify API.

## Features

- **Location-based scraping** — browse deals for any US city (New York, LA, Chicago, Miami, and more)
- **Category filtering** — filter by Things to Do, Beauty & Spas, Food & Drink, Health & Fitness, Automotive, Travel, Goods, Coupons, and more
- **Keyword search** — search for specific deal types like "massage", "restaurant", "oil change", or "escape room"
- **Full price extraction** — original price, deal price, discount percentage, and dollar savings
- **Merchant intelligence** — merchant name, address, phone, website, and location
- **Rating and reviews** — star ratings, review counts, and sold/bought counts
- **Detail page scraping** — optionally visits each deal page for full description, fine print, highlights, redemption instructions, all images, and deal option variants
- **Multi-source extraction** — parses JSON-LD structured data, embedded Next.js state, and raw HTML for maximum data coverage
- **Auto-pagination** — automatically crawls through all result pages up to your limit
- **Anti-bot protection** — User-Agent rotation, respectful rate limiting, CAPTCHA detection
- **Proxy support** — works with Apify proxy for large-scale scrapes
- **PPE pricing** — pay only for what you scrape ($0.004 per deal)

## Input Parameters

| Parameter | Type | Default | Description |
| --- | --- | --- | --- |
| `locations` | string[] | `["new-york"]` | City slugs to scrape (e.g. `new-york`, `los-angeles`, `chicago`) |
| `category` | enum | `"all"` | Category filter: `all`, `things-to-do`, `beauty-and-spas`, `health-and-fitness`, `food-and-drink`, `automotive`, `home-services`, `personal-services`, `retail`, `travel`, `goods`, `coupons` |
| `searchTerms` | string[] | `[]` | Keywords to search (each triggers a separate search per location) |
| `maxResults` | integer | `500` | Maximum total deals to scrape (1-10000) |
| `scrapeDetails` | boolean | `true` | Visit each deal's detail page for richer data |
| `maxConcurrency` | integer | `3` | Concurrent requests (1-10, lower = safer) |
| `proxyConfiguration` | object | `null` | Apify proxy settings |

### Supported Location Slugs

Use the city's URL-friendly slug. Common examples:

| City | Slug |
| --- | --- |
| New York | `new-york` |
| Los Angeles | `los-angeles` |
| Chicago | `chicago` |
| Houston | `houston` |
| Miami | `miami` |
| San Francisco | `san-francisco` |
| Seattle | `seattle` |
| Denver | `denver` |
| Boston | `boston` |
| Atlanta | `atlanta` |
| Dallas | `dallas` |
| Phoenix | `phoenix` |
| Philadelphia | `philadelphia` |
| San Diego | `san-diego` |
| Austin | `austin` |
| Las Vegas | `las-vegas` |
| Portland | `portland-or` |
| Minneapolis | `minneapolis` |
| Nashville | `nashville` |
| Washington DC | `washington-dc` |

## Example Input

### Browse all deals in New York

```
{
  "locations": ["new-york"],
  "category": "all",
  "maxResults": 100
}
```

### Search for spa deals in multiple cities

```
{
  "locations": ["los-angeles", "san-francisco", "san-diego"],
  "category": "beauty-and-spas",
  "searchTerms": ["massage", "facial", "spa day"],
  "maxResults": 500,
  "scrapeDetails": true
}
```

### Food & drink deals nationwide

```
{
  "locations": ["new-york", "chicago", "miami", "houston", "atlanta"],
  "category": "food-and-drink",
  "maxResults": 1000
}
```

### Coupons only (no detail pages for speed)

```
{
  "locations": ["new-york"],
  "category": "coupons",
  "maxResults": 200,
  "scrapeDetails": false
}
```

## Output Format

Each scraped deal produces a JSON object. The fields available depend on whether detail page scraping is enabled.

### Listing Data (scrapeDetails: false)

```
{
  "title": "60-Minute Swedish or Deep-Tissue Massage at Serenity Spa",
  "originalPrice": 120.00,
  "discountPrice": 59.99,
  "discount": "50% OFF",
  "savings": 60.01,
  "merchant": "Serenity Spa & Wellness",
  "rating": 4.7,
  "reviewCount": null,
  "soldCount": 1250,
  "category": "Beauty & Spas",
  "expiresAt": "Expires Mar 30, 2026",
  "description": null,
  "finePrint": null,
  "merchantAddress": null,
  "merchantPhone": null,
  "images": ["https://img.grouponcdn.com/deal/abc123/960x576/image.jpg"],
  "url": "https://www.groupon.com/deals/serenity-spa-massage-1",
  "dealId": "abc-123-def-456",
  "location": "new-york",
  "searchTerm": "massage",
  "searchPage": 1,
  "dataSource": "listing",
  "scrapedAt": "2026-03-01T12:00:00.000Z"
}
```

### Full Detail Data (scrapeDetails: true)

```
{
  "title": "60-Minute Swedish or Deep-Tissue Massage at Serenity Spa",
  "originalPrice": 120.00,
  "discountPrice": 59.99,
  "discount": "50% OFF",
  "savings": 60.01,
  "merchant": "Serenity Spa & Wellness",
  "rating": 4.7,
  "reviewCount": 328,
  "soldCount": 1250,
  "category": "Beauty & Spas",
  "expiresAt": "Expires Mar 30, 2026",
  "description": "Relax with a 60-minute Swedish or deep-tissue massage from a licensed therapist. Includes hot towel treatment and aromatherapy oils. Located in downtown Manhattan with convenient subway access.",
  "finePrint": "Limit 3 per person. Valid Mon-Fri only. By appointment only. New customers only. Must present Groupon voucher upon arrival. Not valid with other offers.",
  "highlights": [
    "60-minute massage session",
    "Choice of Swedish or deep-tissue",
    "Hot towel treatment included",
    "Licensed and certified therapists"
  ],
  "merchantAddress": "123 Broadway, New York, NY 10001",
  "merchantPhone": "(212) 555-0123",
  "merchantWebsite": "https://www.serenityspa.example.com",
  "images": [
    "https://img.grouponcdn.com/deal/abc123/960x576/main.jpg",
    "https://img.grouponcdn.com/deal/abc123/960x576/interior.jpg",
    "https://img.grouponcdn.com/deal/abc123/960x576/room.jpg"
  ],
  "options": [
    {
      "title": "60-Minute Swedish Massage",
      "discountPrice": 59.99,
      "originalPrice": 120.00,
      "discount": "50% OFF"
    },
    {
      "title": "90-Minute Deep-Tissue Massage",
      "discountPrice": 89.99,
      "originalPrice": 180.00,
      "discount": "50% OFF"
    }
  ],
  "redemptionInstructions": "Present your Groupon voucher at the front desk. Must book appointment 24 hours in advance by calling (212) 555-0123.",
  "url": "https://www.groupon.com/deals/serenity-spa-massage-1",
  "dealId": "abc-123-def-456",
  "location": "new-york",
  "dataSource": "detail",
  "scrapedAt": "2026-03-01T12:00:00.000Z"
}
```

## Output Fields Reference

| Field | Type | Description |
| --- | --- | --- |
| `title` | string | Deal headline / title |
| `originalPrice` | number | Regular retail price (before discount) |
| `discountPrice` | number | Groupon deal price |
| `discount` | string | Discount percentage (e.g. "50% OFF") |
| `savings` | number | Dollar amount saved |
| `merchant` | string | Business/merchant name |
| `rating` | number | Star rating (1-5 scale) |
| `reviewCount` | number | Number of reviews |
| `soldCount` | number | Number of vouchers sold/bought |
| `category` | string | Deal category |
| `expiresAt` | string | Expiration date/text |
| `description` | string | Full deal description (detail page only) |
| `finePrint` | string | Terms, conditions, and restrictions (detail page only) |
| `highlights` | string[] | Key deal highlights (detail page only) |
| `merchantAddress` | string | Business street address (detail page only) |
| `merchantPhone` | string | Business phone number (detail page only) |
| `merchantWebsite` | string | Business website URL (detail page only) |
| `images` | string[] | Deal image URLs |
| `options` | object[] | Deal variants/options with individual prices (detail page only) |
| `redemptionInstructions` | string | How to redeem the voucher (detail page only) |
| `url` | string | Direct link to the Groupon deal page |
| `dealId` | string | Groupon's internal deal ID |
| `location` | string | City slug used for the search |
| `dataSource` | string | `listing`, `detail`, or `listing-fallback` |
| `scrapedAt` | string | ISO 8601 timestamp of when the deal was scraped |

## Use Cases

### Deal Aggregation & Comparison

Build a coupon/deal aggregation service by scraping Groupon deals across multiple cities and categories. Compare similar deals across locations to find the best prices.

### Local Business Intelligence

Monitor local business deals and pricing strategies. Track how often merchants offer deals, their discount depths, sold counts, and rating trends over time.

### Competitor Analysis for Local Businesses

If you run a spa, restaurant, or fitness studio, monitor what competitors are offering on Groupon — their prices, discounts, and customer ratings.

### Price Monitoring & Alerts

Run the scraper on a schedule (daily/weekly) to track deal prices. Set up alerts when specific types of deals drop below a threshold price.

### Market Research

Analyze which deal categories are most popular in different cities. Understand seasonal trends, pricing patterns, and consumer demand signals.

### Lead Generation

Extract merchant contact information (address, phone, website) for local business outreach and B2B marketing campaigns.

### Content Creation

Use deal data to power "best deals" articles, newsletters, or social media content about local offers and savings opportunities.

## Tips for Best Results

1. **Use proxies for large scrapes** — Groupon may block IPs that make too many requests. Enable Apify proxy configuration for scrapes over 100 deals.
2. **Keep concurrency at 3 or below** — Groupon is more aggressive about rate limiting than most sites. Start with concurrency 2-3.
3. **Enable detail scraping for rich data** — Set `scrapeDetails: true` to get full descriptions, fine print, merchant contact info, and all images. This is slower but provides much richer data.
4. **Disable detail scraping for speed** — Set `scrapeDetails: false` if you only need titles, prices, and basic info. This is much faster for large-scale price monitoring.
5. **Use specific search terms** — Targeted searches like "oil change" or "teeth whitening" yield more relevant results than broad category browsing.
6. **Scrape multiple locations in one run** — Pass an array of location slugs to compare deals across cities efficiently.
7. **Schedule recurring runs** — Use Apify Scheduler to run the scraper daily or weekly for ongoing deal monitoring and price tracking.
8. **Check the data source field** — The `dataSource` field tells you whether data came from a listing page, detail page, or a fallback (when the detail page failed). Detail pages have the richest data.

## Legal Disclaimer

This scraper is provided for educational and research purposes. Users are responsible for complying with Groupon's Terms of Service and all applicable laws regarding web scraping and data usage. Always respect robots.txt and rate limits.

## Support

If you encounter issues or have feature requests, please open an issue on the GitHub repository or contact us through the Apify platform.

## Integration — Python

```
from apify_client import ApifyClient

client = ApifyClient("YOUR_API_TOKEN")
run = client.actor("sovereigntaylor/groupon-scraper").call(run_input={
    "searchTerm": "groupon",
    "maxResults": 50
})

for item in client.dataset(run["defaultDatasetId"]).iterate_items():
    print(f"{item.get('title', item.get('name', 'N/A'))}")
```

## Integration — JavaScript

```
import { ApifyClient } from 'apify-client';
const client = new ApifyClient({ token: 'YOUR_API_TOKEN' });

const run = await client.actor('sovereigntaylor/groupon-scraper').call({
    searchTerm: 'groupon',
    maxResults: 50
});

const { items } = await client.dataset(run.defaultDatasetId).listItems();
items.forEach(item => console.log(item.title || item.name || 'N/A'));
```