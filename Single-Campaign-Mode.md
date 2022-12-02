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
For now, campaign assets must be added manually, into src/assets/images or src/assets/text. Eventually, it would be ideal to modify our db schema to accommodate more fields.

**Images**
Images should conform to the following naming scheme:
```bash
campaign-logo.xxx
campaign-background.xxx
campaign-img-1.xxx
campaign-img-2.xxx
campaign-img3.xxx
```

**Text**
Text blurbs can be added in a file called text.json in src/assets/text with the following schema:
```bash
{
  "campaign_tagline": "Some short description or campaign name",
  "campaign_text": "The landing page's text body. Line breaks can be done with '\n'. The page's CSS will take care of making them work."
}
```