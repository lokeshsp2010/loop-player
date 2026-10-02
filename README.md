# Loop

A small music player with repeat-one on by default. No backend, no login, no tracking. It runs in the browser and can be installed as an app (PWA).

## What it plays
- **YouTube link**: plays a video you paste through YouTube's own embedded player, unmodified and visible.
- **My files**: audio files you already own, played from your device. They work offline. Optionally keep a copy in your browser (IndexedDB).
- **Search free music**: Creative Commons tracks from the [Jamendo API](https://devportal.jamendo.com). You use your own free client ID.

Loop does not host, download, extract or convert any music or video.

## Run it
Use a web address. Do not double-click `index.html`, because YouTube embeds need a valid origin.
```bash
python3 -m http.server 8000   # open http://localhost:8000
```

## Deploy for free
Push to GitHub, then Settings → Pages → deploy from the `main` branch.

## Offline
The app shell works offline after the first visit. Songs from "My files" play offline. YouTube and Jamendo need internet.

## Compliance notes (reviewed 2 Oct 2026)
- **YouTube** ([Developer Policies guide](https://developers.google.com/youtube/terms/developer-policies-guide), [Required Minimum Functionality](https://developers.google.com/youtube/terms/required-minimum-functionality)):
  - the official IFrame player is used, at least 200x200, with nothing placed over it
  - no audio extraction, no downloading of YouTube content, no ad blocking
  - YouTube playback pauses when the page is hidden or the player is off-screen, so there is no background play
  - repeat uses the player's own loop function
  - no API key or user data is used. The browser sends its normal Referer header
  - users are pointed to the YouTube Terms of Service and Google Privacy Policy
- **Jamendo** ([API terms](https://devportal.jamendo.com/api_terms_of_use)): free for non-commercial use only. This project must stay free of ads, payments and affiliate links. Tracks show the artist, a Jamendo link and the licence link when available. Each user brings their own client ID, which is never stored in this repo.
- **Your own files** are your responsibility. Only add music you have the right to play.
- Loop is not affiliated with or endorsed by YouTube, Google or Jamendo.

## Stack
Plain HTML, CSS and JavaScript. YouTube IFrame API, Jamendo API, Media Session API (non-YouTube tracks only), service worker, IndexedDB.

## License
MIT. Music and videos remain the property of their owners.
