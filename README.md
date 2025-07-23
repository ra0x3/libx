# libx

A music library export tool.

<img src="https://i.imgur.com/wI5WPCe.png" />

## Dependencies

- [ChakraUI](https://www.chakra-ui.com/)
- [Flask](https://flask.palletsprojects.com/en/stable/)

## Usage

> This project can only be run locally because it can't be approved by the Spotify Developer platform, due to the 
> fact that it "violates Spotify's Terms of Service".
> 
> ‼️ In order to use this project, you'll need secrets for both the frontend and the backend from [ra0x3](https://rashad.wiki).

### Setup

Clone the project

```sh
git clone git@github.com:ra0x3/libx.git
```

#### Frontend

Install the frontend dependencies

```sh
# Navigate to the frontend directory
cd libx/www/libx && yarn install --production
```

#### Backend

Install the backend dependencies

```sh
# Navigate to the root directory
cd libx/
python -m venv venv && pip install pipenv && pipenv install --deploy
```

#### Tunnel

> Unfortunately we have to use an HTTP tunnel for the Spotify API to redirect us back to the app. I'm using [ngrok](https://ngrok.com/).

Start the ngrok tunnel on the same port as the app backend.

```sh
ngrok http 8080
```

#### ‼️ Update settings

Update the `.env` files in both the frontend and backend directories with the proper ngrok URL. 

> You'll also need to add the callback ngrok URL (e.g., `https://e81309ad0a08.ngrok.app/api/spotify/callback`) to your Spotify app settings.

### Run

Rebuild your frontend

```sh
# Navigate to the frontend directory
cd libx/www/libx && yarn build
```

Run the Flask development server - which will serve the frontend.

```sh
# Navigate to the root directory
cd libx/
FLASK_RUN_HOST=0.0.0.0 FLASK_RUN_PORT=8080 FLASK_APP=api/app.py flask run
```
