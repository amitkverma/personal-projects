# Product Detail

> Category: Commerce & Payments

## Purpose
Item imagery, price, options, reviews, and add-to-cart.

## Key Elements
- Image gallery with page dots and zoom
- Title, price, rating summary
- Variant selectors (size/color) with availability per option
- Quantity stepper; sticky add-to-cart CTA
- Collapsible sections: description, specs, shipping, returns
- Reviews preview; related products rail

## States & Variations
- Variant unselected → CTA disabled with inline hint at the selector
- Selected variant changes price/images/stock
- Out of stock → "notify me"; sale pricing; added-to-cart confirmation (sheet or mini-cart)

## Design Notes
- The CTA stays sticky and visible through the entire scroll
- Variant errors belong at the selector ("select a size"), not as a toast at the button
- Answer the top purchase objections (shipping cost/time, returns) before the fold if possible

## Technical Considerations
- Model the variant matrix properly: each combination has its own SKU, price, stock, and images; disable impossible combinations as options are picked
- Re-check stock at add-to-cart time and again at checkout — listing-page stock is always stale
- Deep links should support product ID + preselected variant for ads and shares
- Reviews and related products load lazily; don't block the primary content on them
- Emit view_item / add_to_cart with value and currency for funnel and ads attribution

## References
- Amazon, Nike product pages (Mobbin)
