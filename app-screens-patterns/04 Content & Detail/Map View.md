# Map View

> Category: Content & Detail

## Purpose
Geographic display of items or status with pins and a detail callout.

## Key Elements
- Map canvas with pins/markers, clustered at low zoom
- My-location button; "search this area" affordance after panning
- Bottom sheet or card for the selected item
- Map/list toggle

## States & Variations
- Locating (permission granted, acquiring fix)
- Permission denied → default region + manual search
- No results in viewport; loading pins for a new viewport
- Selected pin with detail card; offline (cached tiles or graceful degrade)

## Design Notes
- The bottom-sheet detail keeps map context visible — better than navigating away
- Always offer a list alternative; maps are terrible for comparing many options
- Cluster badges must show counts and split on zoom

## Technical Considerations
- SDK choice (MapKit / Google Maps / Mapbox) drives cost, offline support, and styling freedom — decide early
- Fetch pins by viewport with debounce on pan/zoom; cancel superseded requests
- Cluster client-side for hundreds of points, server-side for thousands
- Recycle marker views; custom marker rendering is a common jank source
- Location permission: request when-in-use only when needed; stop location updates on background to save battery
- Test on the smallest supported device — maps are memory-hungry

## References
- Airbnb, Zenly map patterns (Mobbin)
