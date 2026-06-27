# QiblaView — Improvement Checklist

## Bugs

- [x] **Fix broken photo credit links** — Every face in `facePhotos` has `credit: ''` and `creditUrl: ''`, causing a broken `— View source` link to appear for all users. Populate the fields or remove the credit line entirely.
- [ ] **SVG Kaaba graphic shows wrong faces for S / SW / W / SE directions** — The isometric SVG only has two visible faces (NW and NE). For directions that face the back of the Kaaba the code just dims both panels, which doesn't represent the correct face. Either rotate the SVG to always face the viewer, or add a clear label like "You face the rear of the Kaaba" as a fallback.
- [x] **Remove unused `.direction-arrow` CSS** — The class is styled but no element with that class is ever added to the DOM. Clean it up or wire it up.

---

## High Priority Features

- [ ] **"Use My Location" GPS button** — Add a button that calls `navigator.geolocation.getCurrentPosition()` and pipes the result through the existing `reverseGeocode()` + `processCoords()` functions. Most users want their actual current location, not a typed city.
- [x] **URL sharing / deep linking** — Support `?city=London` or `?lat=51.5&lng=-0.1` query params so results can be bookmarked and shared. The app currently loses all state on every page load.

---

## Medium Priority

- [x] **Escape key closes modals** — Neither the Settings panel nor the About modal respond to the Escape key. Add a `keydown` listener on `document` that closes whichever modal is open.
- [x] **Mirror mosque toggle into Settings panel** — Added "Show holy mosques" toggle to Settings panel (Map group). Both the map panel checkbox and the settings toggle stay in sync via `showMosques` / localStorage.
- [x] **Add meta tags and favicon** — No `<meta name="description">`, no Open Graph tags (`og:title`, `og:image`, `og:url`), and no favicon. Shared links have no preview. A simple Kaaba silhouette or crescent as a favicon would help.

---

## Low Priority / Enhancements

- [ ] **Mobile compass integration** — Use the `DeviceOrientationEvent` API on mobile to show a live needle pointing toward Qibla. Extremely useful for someone standing in a room trying to find the direction in real time.
- [ ] **Prayer times** — Show today's prayer times for the searched city using a free API (e.g. aladhan.com). A natural companion to the Qibla direction for someone preparing for salah.
- [x] **Modal accessibility (focus trapping + ARIA)** — Modals should trap Tab focus inside while open. Both modals also need `role="dialog"`, `aria-modal="true"`, and `aria-labelledby` pointing to their title element.
