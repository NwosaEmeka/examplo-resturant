# centralapp

A plain HTML test site that looks like a CentralApp restaurant site and loads the
deployed UMAI widget (staging, KWC Singapore key) in two ways:

- **No button** (`index.html`): a plain `<iframe>` on the staging `embed-frame.html` with
  `frame_mode=inline`, no UMAI script on the page. The widget renders on load, with no
  click needed.
- **Button** (`booking.html`): `data-frame-embed="modal"` with the floating button off,
  and the venue's own "Book now" button calling `window.umaiWidget.openWidget()`.

`menu.html` has no widget. Shared styles are in `styles.css`.

## Run

Serve it over http. Opened as `file://`, the page origin is `null` and the frame
handshake fails.

```sh
cd ~/codes/umai/centralapp
python3 -m http.server 5500
# open http://localhost:5500
```

To try another venue or environment, edit `data-api-key` or the script `src` in the
page. Don't use a real venue's production key with the production script unless you
mean to: bookings made there are real reservations.
