[Groupon Scraper](https://apify.com/saswave/groupon-scraper?fpr=data)

## Groupon Web Scraper

Extract complete product, pricing, merchant and customer-review data from Groupon marketplaces worldwide.

Works on:

groupon.com

groupon.fr

groupon.co.uk

groupon.de

All Groupon subdomains

Turn Groupon listings into structured e-commerce datasets.

## 🚀 What This Scraper Does

This crawler extracts products, sellers, reviews, and suggestions from Groupon category pages, deal URLs, and search result pages.

It supports:

Category crawls

Product-level scraping

Related products (suggestions)

Merchant info

Customer reviews

## ✅ Extracted Data

Depending on input type, you can extract:

## 🛒 Product information

Product name

Deal URL

Pricing (current & original)

Discount %

Currency

Category & breadcrumb

Rating

Sales count

Views in last 24h

Images

Badges (Best seller, Popular gift, etc.)

Shipping info

Inventory identifiers

Variations / models

Deal urgency messages

## 🏪 Merchant data

Merchant name

Seller website

Merchant description (when available)

## ⭐ Reviews

Review text

Rating

Date

Reviewer name

Reviewer profile

Merchant reply (if available)

Review helpfulness

Redeemed date

## 🔁 Suggestions

Related / similar products

Look-alike recommendations

Alternative offers

Discount comparisons

## Ouput example

Product from search url

```
{
  "input_ref_page_url": "https://www.groupon.fr/goods/bagages",
  "input_ref_page_number": 1,
  "item_id": "d59aa2f0-c27f-4267-8a64-755d6579d89e",
  "rating": 5,
  "currency": "EUR",
  "category": "Luggage Sets",
  "categories_breadcrumb": "Goods > For the Home > Luggage > Luggage Sets",
  "inventory_service_id": "goods",
  "restricted_reason": "[]",
  "restricted": 0,
  "show_discount": 1,
  "eligible_for_groupon_incentives": 1,
  "pds_id": "39a3ab07-83f8-4b68-b187-bc7e9098ee7d",
  "channel_id": "92868e9f-7561-4515-bd0c-653d44ab51a6",
  "inventory_product_id": "993011aa-ac6c-4095-b3d7-fbb8c1c46c67",
  "minimum_purchase_quantity": 1,
  "_customer_item_id": "d59aa2f0-c27f-4267-8a64-755d6579d89e",
  "channel": "shopping",
  "is_bookable": 0,
  "is_travel_bookable_deal": 0,
  "med_image": "https://img.grouponcdn.com/deal/3Zmockwfb3UzVCr4RToaG1aZ9rPf/3Z-2048x1229/v1/t300x182.jpg",
  "merchant_name": "Halterner Technologie GmbH",
  "purchases_total_displayed": 229,
  "url": "https://www.groupon.fr/deals/ensemble-valises-rigides-abs-1",
  "views_24h": 85,
  "title": "Ensemble de valises rigides en ABS, coloris au choix, livraison offerte",
  "models": [
    {
      "title": "Ensemble de valises rigides en ABS : Gris et marron",
      "discount_percent": 55,
      "current_price": 12000,
      "original_price": 26549
    },
    {
      "title": "Ensemble de valises rigides en ABS : Crème",
      "discount_percent": 55,
      "current_price": 12000,
      "original_price": 26549
    },
    {
      "title": "Ensemble de valises rigides en ABS : Noir et marron",
      "discount_percent": 55,
      "current_price": 12000,
      "original_price": 26549
    }
  ]
}
```

Product from input

```
{
  "title": "Livre photo classique en format A3 horizontal de 28 à 140 pages, avec Colorland (jusqu'à 65% de réduction)",
  "rating": "4.5",
  "reviews": "1,592",
  "original_price": "49,99 €",
  "current_price": "27,95 €",
  "discount_message": "44% de réduction",
  "sold_message": "460+ acheteurs",
  "variations": {
    "la_quantité_de_pages": [
      "livraison non comprise - 28 pages",
      "livraison non comprise - 40 pages",
      "livraison non comprise - 60 pages",
      "livraison non comprise - 100 pages",
      "livraison non comprise - 120 pages"
    ],
    "la_quantité_de_livres": [
      "x 1",
      "x 2"
    ]
  },
  "shipping": "",
  "badges": [
    "100+ vendus",
    "Cadeau populaire",
    "Meilleure note"
  ],
  "urgency_message": "Plus de 60 vues aujourd'hui, alors achetez dès maintenant !",
  "images": [
    "https://img.grouponcdn.com/deal/2xA3w3jYPiaaoCDzseLiA5XnDeZS/2x-1200x720/v1/sc100x100.webp",
    "https://img.grouponcdn.com/deal/32kNdAnkZ74EHhquLBkN1G5T5WUn/32-1200x720/v1/sc100x100.webp",
    "https://img.grouponcdn.com/deal/YSfq7jM8emxqKw1zsoNvjWvJDst/YS-1200x720/v1/sc100x100.webp",
    "https://img.grouponcdn.com/deal/2CYGA3UQeLr4ozVxHsTr3jpJhKr8/2C-1200x720/v1/sc100x100.webp",
    "https://img.grouponcdn.com/deal/33fq8hs8GqWzKPGbfqLqvkERxcKe/33-1200x720/v1/sc100x100.webp",
    "https://img.grouponcdn.com/deal/HoxhFGuGaWWkV7z1kN2QHbwLsyA/Ho-1200x720/v1/sc100x100.webp",
    "https://img.grouponcdn.com/deal/35qjtgUfVzoVPSx6XVPqUQXQfdN1/35-1200x720/v1/sc100x100.webp"
  ],
  "highlights": [
    "Points forts",
    "Créer son propre livre photo entièrement personnalisable avec une couverture rigide ou souple"
  ],
  "about": [
    "À propos de ce deal",
    "Après avoir acheté ce deal, vous devriez visiter le site Web indiqué sur votre coupon pour compléter votre achat.",
    "Ce qui est inclus : 1 ou 2 livres photos à personnaliser sur le site Colorland",
    "Ce qui est inclus",
    ": 1 ou 2 livres photos à personnaliser sur le site Colorland",
    "Format : A3",
    "Nombre de pages possibles : 28, 40, 60, 100 ou 120",
    "Comment utiliser votre coupon",
    "1. Après l'achat, rendez-vous sur votre espace personnel Groupon / Mes commandes.",
    "2. Cliquez sur \"Voir les détails\".",
    "3. Cliquez sur le bouton bleu Reedem Online  / Utilisez le coupon. Vous serez redirigé vers le site de Colorland.",
    "4.Connectez-vous à votre espace client ou créez votre compte Colorland. Votre code s'enregistre automatiquement dans le panier dans l’onglet « Codes promo ».",
    "5. Cliquez sur le bouton jaune \"Créez votre produit\" et commencez votre création en cliquant sur \"Créez\".",
    "6. Une fois terminée, dans le panier, insérez votre code. Vous le trouverez en gras dans l’onglet «  Codes promo ».\nCopiez / Collez le code dans le champ « Avez-vous le code de réduction? ».",
    "7. Complétez vos informations puis procédez au règlement des frais de port.",
    "SAV :",
    "après votre commande en cas de questions, contactez le vendeur par mail à",
    "info.fr@colorland.com",
    "en ajoutant votre coupon en pièce jointe ou par téléphone au 04 26 99 00 96."
  ],
  "fine_print": [
    "Conditions",
    "Validité :",
    "dès la réception de votre coupon, vous avez 3 mois après la date d'achat pour valider votre commande en ligne sur le site de",
    "Colorland",
    ".",
    "Livraison :",
    "sous 10 jours ouvrés en France métropolitaine (hors DOM-TOM et Corse) après validation de votre commande. Frais de port en sus : 8,95 € pour 1 livre, 9,95 € pour 2 livres.",
    "Autres conditions :",
    "plusieurs coupons par personne peuvent être achetés et échangés. Une fois l'achat effectué sur le site du vendeur aucune annulation ne sera possible. Valide uniquement pour l'option achetée.",
    "Voir la",
    "Politique de retour de Groupon France SAS",
    "Comment ça marche",
    "1. Après l'achat, rendez-vous sur votre espace personnel Groupon / Mes commandes.",
    "2. Cliquez sur \"Voir les détails\".",
    "3. Cliquez sur le bouton bleu \"Redeem Online\"  / Utilisez le coupon. Vous serez redirigé vers le site de Colorland.",
    "4.Connectez-vous à votre espace client ou créez votre compte Colorland. Votre code s'enregistre automatiquement dans le panier dans l’onglet \"Codes promo\".",
    "5. Cliquez sur le bouton jaune \"Créez votre produit\" et commencez votre création en cliquant sur \"Créez\".",
    "6. Une fois terminée, dans le panier, insérez votre code. Vous le trouverez en gras dans l’onglet \"Codes promo\". \nCopiez / Collez le code dans le champ \"Avez-vous le code de réduction ?\".",
    "7. Complétez vos informations puis procédez au règlement des frais de port.",
    "SAV :",
    "après votre commande en cas de questions, contactez le vendeur par mail à",
    "info.fr@colorland.com",
    "en ajoutant votre coupon en pièce jointe ou par téléphone au 04 26 99 00 96."
  ],
  "promo_message": [
    "2.8 € de réduction",
    "Code ",
    "PROMO",
    ". Expire le 17/3."
  ],
  "merchant_name": "Colorland",
  "merchant_about": {
    "merchant_website": "https://www.colorland.com/fr/"
  },
  "input_ref_page_url": "https://www.groupon.fr/deals/colorland-1148",
  "input_ref_page_number": ""
}
```

Product suggestions

```
{
  "input_ref_page_url": "https://www.groupon.fr/deals/colorland-1148",
  "input_ref_page_number": "",
  "item_id": "69224453-f984-4d21-aa5d-c8d1c377fe7e",
  "rating": 0.23890755898000254,
  "currency": "EUR",
  "category": "",
  "categories_breadcrumb": "",
  "inventory_service_id": "vis",
  "restricted_reason": "[]",
  "restricted": 0,
  "show_discount": 1,
  "eligible_for_groupon_incentives": 1,
  "pds_id": "e45f6c29-3d46-46f7-864a-ee45d08b0097",
  "channel_id": "2064915a-347c-410d-a18a-76556d5540fe",
  "inventory_product_id": "a1d5513f-a6cd-4f70-bd54-9f1db44ad1a9",
  "minimum_purchase_quantity": 1,
  "_customer_item_id": "69224453-f984-4d21-aa5d-c8d1c377fe7e",
  "channel": "local",
  "is_bookable": 0,
  "is_travel_bookable_deal": 0,
  "med_image": "https://img.grouponcdn.com/deal/2FwmvaEJJyap7kMzk3UmAnqXK5bb/2F-1500x900/v1/t300x182.jpg",
  "merchant_name": "Printerpix FR",
  "purchases_total_displayed": 244,
  "url": "https://www.groupon.fr/deals/printerpix-fr-1-7648301",
  "views_24h": 4,
  "title": "Immortalisez vos souvenirs : livre(s) photo Printerpix A4 ou A5 de 30, 50 ou 100 pages (jusqu'à 87% de remise)",
  "models": [
    {
      "title": "Livraison non comprise - 1 livre photo A4 à couverture rigide de 100 pages",
      "discount_percent": 82,
      "current_price": 2499,
      "original_price": 13995
    },
    {
      "title": "Livraison non comprise - 3 livres photo A4 à couverture rigide de 30 pages",
      "discount_percent": 82,
      "current_price": 3499,
      "original_price": 19485
    },
    {
      "title": "Livraison non comprise - 2 livres photo A5 à couverture rigide de 50 pages",
      "discount_percent": 85,
      "current_price": 1999,
      "original_price": 12990
    },
    {
      "title": "Livraison non comprise - 1 livre photo A5 à couverture rigide de 100 pages",
      "discount_percent": 87,
      "current_price": 1499,
      "original_price": 11495
    },
    {
      "title": "Livraison non comprise - 3 livres photo A5 à couverture rigide de 30 pages",
      "discount_percent": 84,
      "current_price": 2099,
      "original_price": 13485
    },
    {
      "title": "Livraison non comprise - 2 livres photo A4 à couverture rigide de 100 pages",
      "discount_percent": 82,
      "current_price": 4999,
      "original_price": 27990
    },
    {
      "title": "Livraison non comprise - 3 livres photo A4 à couverture rigide de 100 pages",
      "discount_percent": 82,
      "current_price": 7399,
      "original_price": 41985
    },
    {
      "title": "Livraison non comprise - 1 livre photo A4 à couverture rigide de 30 pages",
      "discount_percent": 82,
      "current_price": 1199,
      "original_price": 6495
    },
    {
      "title": "Livraison non comprise - 1 livre photo A4 à couverture rigide de 50 pages",
      "discount_percent": 82,
      "current_price": 1699,
      "original_price": 9495
    },
    {
      "title": "Livraison non comprise - 1 livre photo A5 à couverture rigide de 30 pages",
      "discount_percent": 84,
      "current_price": 699,
      "original_price": 4495
    },
    {
      "title": "Livraison non comprise - 2 livres photo A5 à couverture rigide de 30 pages",
      "discount_percent": 84,
      "current_price": 1399,
      "original_price": 8990
    },
    {
      "title": "Livraison non comprise - 2 livres photo A4 à couverture rigide de 50 pages",
      "discount_percent": 83,
      "current_price": 3299,
      "original_price": 18890
    },
    {
      "title": "Livraison non comprise - 2 livres photo A4 à couverture rigide de 30 pages",
      "discount_percent": 82,
      "current_price": 2299,
      "original_price": 12990
    },
    {
      "title": "Livraison non comprise - 3 livres photo A4 à couverture rigide de 50 pages",
      "discount_percent": 82,
      "current_price": 4999,
      "original_price": 28485
    },
    {
      "title": "Livraison non comprise - 1 livre photo A5 à couverture rigide de 50 pages",
      "discount_percent": 85,
      "current_price": 999,
      "original_price": 6495
    },
    {
      "title": "Livraison non comprise - 3 livres photo A5 à couverture rigide de 50 pages",
      "discount_percent": 85,
      "current_price": 2999,
      "original_price": 19485
    }
  ],
  "suggestion_type": "lookalike"
}
```

Reviews

```
{
  "collapseText": true,
  "createdDate": "il y a 3 jours",
  "id": "175569ac-002c-11f0-9f54-0642ef71a6b3",
  "isLiked": null,
  "likeCount": null,
  "merchantName": "Colorland",
  "merchantReply": null,
  "rating": 5,
  "redeemedAt": "Utilisé : il y a 4 jours",
  "reviewText": "Bon rapport Qualité / prix",
  "starIcons": [
    "full-star",
    "full-star",
    "full-star",
    "full-star",
    "full-star"
  ],
  "user": {
    "initials": "M",
    "maskedName": "Marite",
    "profileId": "58c890c7-19ca-11e9-833d-a0369f58f9f0",
    "stats": {
      "reviewCount": 28,
      "helpfulCount": 1,
      "imageCount": 0,
      "ratingCount": 36,
      "badges": [
        {
          "badgeText": "Top contributeur",
          "tooltip": false
        }
      ]
    },
    "wroteReviewForText": null
  },
  "input_ref_page_url": "https://www.groupon.fr/deals/colorland-1148",
  "input_ref_page_number": ""
}
```

## 🎯 Use Cases

Price monitoring

Product intelligence

Competitor tracking

Review sentiment analysis

Merchant research

Deal comparison engines

Affiliate marketing tools

E-commerce analytics

Drop-shipping research

Market trend analysis

## ⚠ Limitations & Notes

Data varies by country

Listings may differ based on location

Some sellers hide analytics

Availability may change in real time

Deals may expire or be restricted

## ✅ Best Practices

Use direct product URLs when possible

Category URLs return multiple products

Monitor expiration fields

Save merchant keys for deduplication

Normalize prices into cents

Track discounts over time for trend analysis

## 🛟 SUPPORT

Share your runs with the developer team and create issues on error to help us improve actor quality.

You might discover edge case we didn't test yet

We stay available anytime