# Vimeo Player iOS Issue

Run alongside a Flutter Project, with this as the `main.dart`: https://gist.github.com/giordanna/938ee0c301a19a0068d03ca29ace2300

This vimeo ID words fine on an iOS app: 666201451, while this one gives an error: 855303737.

### Vimeo Issue
```
Title: Newer videos are not working on Vimeo Player on Flutter using InAppWebView on iOS

Body:
Our application consists of a website displayed inside Flutter using the InAppWebView Plugin. Inside we use Vimeo Player to allow users to watch our training courses. It works fine on almost everywhere except on iOS devices. It even works on Safari but not on Flutter.
We tried searching anywhere for similar issues with no luck, and there are no log errors when this happens. We also tried setting the same configurations from our working videos to the not working ones, but again, no luck.
I created a minimal reproduction on Github, here's the repo: https://github.com/giordanna/vimeo-player-ios-issue-svelte and here's on GH pages: https://giordanna.github.io/vimeo-player-ios-issue-svelte/. And the main.dart gist from Flutter: https://gist.github.com/giordanna/938ee0c301a19a0068d03ca29ace2300. I tried my best to simplify the Flutter file so it's reproducible.
For instance, this vimeo ID words fine on our iOS app: 666201451, while this one gives an error: 855303737.
We don't know if the issue is on Vimeo itself or on InAppWebView Plugin. If it's on the latter we will also open an issue there. Meanwhile, we let our users watch the videos on their browsers if the video is not working on the app.
```

## Developing

```bash
npm i

npm run dev

# or start the server and open the app in a new browser tab
npm run dev -- --open
```

## Building

```bash
npm run build
```

You can preview the production build with `npm run preview`.

