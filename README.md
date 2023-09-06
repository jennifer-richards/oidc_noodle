# oidc_noodle
Proof-of-concept Django OIDC auth using mozilla-django-oidc

## Installation
1. Run a local copy of datatracker in Docker. In the admin, add an OpenID Connect Provider client. Settings are
   - Client type: confidential
   - Response type: code (authorization code flow)
   - Redirect URI: `http://localhost:8888/oidc/callback/`
   - JWT algorithm: RS256
   - Scopes: `openid profile email`
2. Create `secrets.env` like
```
# Do not commit this file!
POSTGRES_PASSWORD=<whatever you want>
OIDC_RP_CLIENT_ID=<client id from step 1>
OIDC_RP_CLIENT_SECRET=<client secret from step 1>
```
3. Start this docker compose stack
4. Open `http://localhost:8888`, click "Login", and authenticate with some datatracker user.

If this works, you will be redirected to a page that identifies you with the primary email address of the user you authenticated with.
