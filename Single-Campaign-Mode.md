# Single Campaign Mode

Amplify now supports a 'single campaign' mode for deployments. This mode exposes a landing page for the featured campaign and allows for overriding the representative search to curate a campaign's reach.

Development is still ongoing so please create an issue if you want to suggest an improvement or report a bug.

## Enabling Single Campaign mode
Single Campaign Mode (SCM) will be enabled after setting the following environment variables:
```bash
VUE_APP_CAMPAIGN_MODE = "single" (for SCM) || "default" (for normal mode)
VUE_APP_FEATURED_CAMPAIGN = "campaign id from Postgres"
VUE_APP_LETTER_TEMPLATE = "The lob template of the letter you wish to load"
```

## Adding Campaign Assets
For now, campaign assets must be added manually into src/assets/images or src/assets/text. Eventually, it would be ideal to modify our db schema to accommodate more fields.

**Images**

Images should conform to the following naming schema:
```bash
campaign-logo.webp
campaign-background.webp
campaign-img-1.webp (should be around 350x255)
campaign-img-2.webp
campaign-img-3.webp
```
Amplify will expect .webp files. Use [Google's webp conversion tool](https://developers.google.com/speed/webp/docs/precompiled) or some similar utility.

**Text**

Text blurbs can be added in a file called text.json in src/assets/text with the following schema:
```bash
{
  "campaign_tagline": "Some short description or campaign name",
  "campaign_text": "The landing page's text body. Line breaks can be done with '\n'. The page's CSS will take care of making them work."
}
```

## Overriding Brand Colors
Amplify now supports custom branding for SCM. To override styles, modify /src/configs/theme.js.
```bash
// Dark theme support coming soon!

const lightTheme = {
  'primary': '#083d77',
  'primary-alt': '#38618c',
  'secondary': '#fe5e41',
  'secondary-alt': '#fcd7ad',
  'tertiary': '#F3B700',
  'tertiary-alt': '#080085',
  'dark': '#333333',
  'med-gray': '#bbbbbb',
  'light-gray': '#eeeeee',
  'white': '#ffffff',
}
```
Less variables with the corresponding names (ex. @secondary-alt, @dark, etc.) will also be available globally.

**A note on text contrast:** You may want to tweak some of the text if you find the contrast with a custom color is too low. Vuetify does a pretty good job of switching colors on some things like v-btns, but in other instances, manual intervention yields a better result.