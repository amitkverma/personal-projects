# Checkout

> Category: Commerce & Payments

## Purpose
Address, delivery, and payment method entry before placing the order.

## Key Elements
- Address selection/entry with autocomplete
- Delivery-option chooser with dates and prices
- Payment methods: Apple Pay / Google Pay first, then cards, saved methods
- Compact order summary; place-order CTA with total on the button

## States & Variations
- Single-page vs stepped checkout
- Address validating / invalid
- Payment authenticating (3DS challenge) / processing / declined with reason
- Success → confirmation handoff

## Design Notes
- Apple Pay/Google Pay first: one tap beats any form
- Never lose entered data on an error — restore everything
- Guest checkout matters; forcing account creation before payment costs real revenue

## Technical Considerations
- Use a payment provider SDK (Stripe/Adyen/Braintree): card data goes straight from SDK to provider and never touches your servers, keeping you out of most PCI scope
- Payment intents with idempotency keys — network retries must never double-charge
- Implement 3DS/SCA challenge flows; they are mandatory in many regions and a common drop-off point to instrument
- Order placement as an atomic server-side transaction: reserve stock → capture/authorize → confirm, with compensating rollback on failure
- Address validation/autocomplete service (e.g. Google Places) reduces failed deliveries
- Apple Pay requires merchant ID + certificates and real-device testing; Google Pay has an equivalent setup path

## References
- Stripe mobile checkout guides; Shop app checkout (Mobbin)
