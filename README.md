# spotipy-fastapi-oauth
This is a simple example of using Spotipy with FastAPI with multi-user support.

> [!CAUTION]
> I have no experience with FastAPI and this was pretty much the first time in two years that I've written anything with FastAPI.

## Setup

1. Clone the repository
2. Install the requirements with `pip install -r requirements.txt`
3. Configure `config.toml`.
4. start the application with `python -m uvicorn main:app --host 0.0.0.0 --port 15912` or similar.

## Endpoints

### Root (`/`)

Returns the user data (`spotipy.Spotify.me()`) if the user is logged in. If not, a 401 Unauthorised with the auth_url will be returned.

### Callback (`/callback`)

After logging in with Spotify, the user should be redirected to this endpoint. If all goes well, the user will be redirected to root.

### Logout (`/logout`)

Removes the session from the fake database (but not the cookies). Returns code 200 and `{"detail": "success"}` and the user must re-authenticate.
