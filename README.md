## Pelican Panel + Pocket ID OAuth

Add the Pocket ID OAuth provider to the Pelican Panel image. This repo builds a Docker image that vendors the `socialiteproviders/pocketid` package and registers a new `PocketIDSchema` with the Panel, enabling sign-in via your Pocket ID instance.

---

## Quick start

### 1) Build the image
```bash
docker build -t pelican-panel-pocketid .
```

Optionally tag for your registry:
```bash
docker tag pelican-panel-pocketid ghcr.io/<your-org>/pelican-panel:pocketid
docker push ghcr.io/<your-org>/pelican-panel:pocketid
```

### 2) Configure environment

These environment variables control the Pocket ID integration (also you can configure it through admin panel):

- **OAUTH_POCKETID_BASE_URL**: Base URL of your Pocket ID instance (e.g., `https://id.example.com`)
- **OAUTH_POCKETID_CLIENT_ID**: OAuth client ID issued by Pocket ID
- **OAUTH_POCKETID_CLIENT_SECRET**: OAuth client secret issued by Pocket ID
- **OAUTH_POCKETID_DISPLAY_NAME** (optional): Provider label shown on the login button; default: `Pocket ID`
- **OAUTH_POCKETID_DISPLAY_COLOR** (optional): Hex color for the button; default: `#000000`

### 3) Configure redirect/callback in Pocket ID

In your Pocket ID application settings, set the OAuth redirect/callback URL to your Panel domain using the `pocketid` provider slug, for example:

- `https://<your-panel-domain>/auth/oauth/callback/pocketid`

After starting the container, the login page should show a Pocket ID button using your configured name and color.

---

## Acknowledgements

- Pelican Panel and its maintainers
- Socialite Providers (`socialiteproviders/pocketid`)
- Pocket ID


*proudly vibecoded by GPT-5, i don't give a fuck.*