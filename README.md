# Ackerman Negotiation Calculator

A small web app that plans a price negotiation for you using the Ackerman model. Type in the price you actually want, and it gives you four offers to make in order, plus a ready-to-say script for each one. It works for buyers and sellers, runs on your phone, and can be installed like a regular app.

## What is the Ackerman model?

The Ackerman model is a step-by-step way to bargain over price. It's best known from Chris Voss, a former FBI hostage negotiator, who describes it in his book *Never Split the Difference*. Voss credits it to Mike Ackerman, a former CIA operative.

The idea is to never jump straight to your real number. You start far from it and move toward it in smaller and smaller steps, so each move feels like the other side is really pulling something out of you.

If you're buying, with a target of 100:

1. Open at 65% of your target
2. Move up to 85%
3. Move up to 95%
4. Offer 100%, and add something that isn't cash

Each jump is smaller than the last, which signals that you're running out of room. The final offer uses an odd-looking number and a non-cash extra (like paying today) to show there's nothing left to give.

If you're selling, it works in reverse: 135%, then 115%, then 105%, then 100% plus a perk.

This app is just a calculator based on that idea. It isn't affiliated with Chris Voss or the book, and I'd recommend reading the book if you want the full picture.

## What the app does

- Buyer and seller modes
- Calculates all four offers from your target price
- Writes a short script for each step that you can read out or paste into a chat
- Final offers get slightly randomized odd endings (3, 7 or 9), so they look calculated instead of rounded
- Lets you mark each step as used so you can keep track during a live negotiation
- Lets you log what the other side offers back, then shows the remaining gap, a simple trend line, and a suggestion for what to do next
- Keeps multiple negotiations saved side by side, so you can switch between them
- Copies the whole plan to your clipboard
- Supports USD, PHP, EUR, GBP, JPY, INR, CNY and AUD
- Installs to your home screen and works offline

Everything is saved in your browser's local storage on your own device. There's no account, no server, and nothing gets sent anywhere.

## Try it

Live version: add your link here (for example `https://ja1rene.github.io/ackerman/`)

## Run it yourself

There's no build step and nothing to install.

```bash
git clone https://github.com/ja1rene/ackerman.git
cd your-repo-name
```

Then serve the folder with any simple web server. For example, with Python:

```bash
python3 -m http.server 8000
```

Open `http://localhost:8000` in your browser.

You can also double-click `index.html` and it will open, but the offline and install features won't work that way. Service workers only run over `http://localhost` or `https://`, not from a file on disk.

## Put it online with GitHub Pages

1. Push the files to your repo
2. Go to **Settings**, then **Pages**
3. Under **Branch**, choose `main` and the `/ (root)` folder, then save
4. After a minute or two it will be live at `https://your-username.github.io/your-repo-name/`

GitHub Pages uses https, so installing and offline mode will work.

## Install it on your phone

- **Android (Chrome):** open the page, tap the menu, then **Install app** or **Add to Home screen**
- **iPhone (Safari):** open the page, tap the share button, then **Add to Home Screen**

## How to use it

1. Pick **Buyer** or **Seller**
2. Choose your currency
3. Enter your target price, which is the number you'd actually be happy with
4. Type what the deal is about (for example "used laptop")
5. Optionally, enter a non-cash extra you can offer at the end, like paying today or free pickup
6. Tap **Generate negotiation plan**
7. Go through the offers one at a time. Say the script, pause, and let the other person answer before moving on
8. When they make a counter-offer, log it in the box at the bottom

A good habit is to stay quiet after each offer. The pause does a lot of the work.

## A note on the "win probability"

The win probability and the suggestions are simple rules of thumb based on how far the other side's latest offer is from your target. They aren't real statistics and they can't predict what a real person will do. Treat them as a nudge, not as advice.

Also, the scripts are meant to be honest framing. Please don't make up a fake budget or a fake backstory to go with them.

## Files

```
index.html          the app (HTML, CSS and JavaScript in one file)
manifest.json       tells the browser how to install it
service-worker.js   caches the files so it works offline
icon.svg            the app icon
```

## Changing it

- **Percentages:** edit the `ladders` object in `index.html`
- **Scripts:** edit the `makeScript` function
- **Currencies:** add an `<option>` to the currency dropdown and a matching entry in `formatCurrency`
- **Colors:** the variables at the top of the CSS (`--bg`, `--blue`, and so on)

If you change any file, bump the version in `service-worker.js` (the `CACHE_NAME` line, for example from `ackerman-app-v3` to `ackerman-app-v4`). Otherwise phones that already installed the app may keep showing the old cached version.

## Credits

The Ackerman model is from Chris Voss's book *Never Split the Difference*, who credits it to Mike Ackerman.

## License

Free to use, copy and change. If you share your own version, a link back is nice but not required.
