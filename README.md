<h1 align="center">roboto</h1>

<div align="center">
	<img src="assets/roboto.png" width="250" title="roboto logo">
</div>


## About

`roboto` is a system designed to function as a "personal internet" for the modern homesteader/researcher/user to support learning and curiosity in many realms. This is an ongoing project that is constantly evolving.

Roboto is currently composed of a weather tracking system (**Air**), a personalized dictionary (**Lexicon**), and a chat application (**wh00t**), including various chatbots. More features are coming to help communicate, perform effective research and take advantage of IoT technologies in order to be able to learn, create, analyze, and communicate all in one place. 

The overall intention for this project is to be able to easily spin up an instance to your liking, for your needs. Roboto can work as a LAN based system or one you host online. You are in control of your data, with easy access to your SQLite databases (you choose their location).


To get started with **roboto**, simply follow the instructions below.


## Demo
- [roboto demo - UI](https://apps.roboto84.dev/)
- [roboto demo - API docs](https://api.roboto84.dev:8000/docs)

<div align="center">
	<img src="assets/roboto_1.png" title="roboto - light mode">
    <br/>
    roboto home - light mode
    <br/><br/>
    <img src="assets/roboto_2.png" title="Air - light mode">
    <br/>
    Air - light mode
    <br/><br/>
    <img src="assets/roboto_3.png" title="Air - dark mode">
    <br/>
    Air - dark mode
    <br/><br/>
    <img src="assets/roboto_4.png" title="Air - charts - dark mode">
    <br/>
    Air - charts - dark mode
    <br/><br/>
    <img src="assets/roboto_5.png" title="Air - charts - light mode">
    <br/>
    Air - charts - light mode
    <br/><br/>
    <img src="assets/roboto_6.png" title="Air - tables - light mode">
    <br/>
    Air - tables - light mode
    <br/><br/>
    <img src="assets/roboto_7.png" title="Lexicon - light mode">
    <br/>
    Lexicon - light mode
    <br/><br/>
    <img src="assets/roboto_8.png" title="Lexicon - dark mode">
    <br/>
    Lexicon - dark mode
    <br/><br/>
    <img src="assets/roboto_9.png" title="wh00t - dark mode">
    <br/>
    wh00t - dark mode
    <br/><br/>
    <img src="assets/roboto_10.png" title="wh00t - Air bot - dark mode">
    <br/>
    wh00t - Air bot - dark mode
    <br/><br/>
    <img src="assets/roboto_11.png" title="wh00t - Lexicon bot - light mode">
    <br/>
    wh00t - Lexicon bot - light mode
    <br/><br/>
    <img src="assets/roboto_12.png" title="wh00t - Arcadia bot - light mode">
    <br/>
    wh00t - Arcadia bot - light mode
    <br/><br/>
    <img src="assets/roboto_13.png" title="wh00t - Arcadia bot - dark mode">
    <br/>
    wh00t - Arcadia bot - dark mode
    <br/><br/>
    <img src="assets/roboto_14.png" title="wh00t - mini chat - light mode">
    <br/>
    wh00t - mini chat - light mode
    <br/><br/>
</div>

## Submodules
- The `roboto` repository consists of the following Git submodules:

    | Repo | URL | Tech | Description
    |------|-----|------|-------------
    | `roboto_ui` | https://github.com/roboto84/roboto_ui | React/Typescript | frontend
    | `roboto_api` | https://github.com/roboto84/roboto_api | Python | backend
    | `air_collect` | https://github.com/roboto84/air_collect | Python | weather collection
    | `wh00t_server` | https://github.com/roboto84/wh00t_server| Python | chat server
    | `air_bot` | https://github.com/roboto84/air_bot | Python | weather chatbot
    | `lexicon_bot` | https://github.com/roboto84/lexicon_bot | Python | dictionary chatbot
    | `gopher_bot` | https://github.com/roboto84/gopher_bot | Python | gopher chatbot
    | `arcadia_bot` | https://github.com/roboto84/arcadia_bot | Python | arcadia chatbot


## Requirements
- [docker](https://docs.docker.com/get-docker/) or [docker-compose standalone](https://docs.docker.com/compose/install/)

## API Keys
In order to setup an instance of `roboto` you must  acquire the following API keys:

- Dictionary data for **Lexicon**:
    - Merriam-Webster Dictionary (**Required**) - https://dictionaryapi.com
    - Oxford Dictory (**Optional**) - https://developer.oxforddictionaries.com
- Weather data for **Air**:
    - Tomorrow.io (**Required**) - https://docs.tomorrow.io/reference/welcome

## Environmental Variables

- The following table details all of the environmental variables that appear in [.env.defaults](.env.defaults):

    | Env | Description | Default
    |-----|-------------|--------
    | `SOCKET_SERVER_PORT` | Port used by chat server (`wh00t_server`). | `3001`
    | `HTTP_SERVER_PORT` | Port used by `roboto_api`. | `8000`
    | `AIR_LOCATION` | The name of the location you want to collect weather for. | `Gainesville, FL`
    | `TIMEZONE` | The timezone you want `roboto_ui` to use. | `US/Eastern`
    | `COORDINATE_LAT` | Latitude of the location you want to collect weather for. Goto https://www.latlong.net/ for assistance. | `29.651634`
    | `COORDINATE_LONG` | Longitude of the location you want to collect weather for. Goto https://www.latlong.net/ for assistance. | `-82.324829`
    | `QUERY_API_INTERVAL` | The amount of seconds to wait before querying the weather API, i.e. polling interval. | `3600`
    | `NUM_OF_LIVE_READINGS` | The max number of weather data rows the *live data* csv file should hold at any given time. This does not impact the SQLite DB, as it collects all readings without limits. | `100`
    | `LOG_LOCATION` | Where logs are stored. | `./logs`
    | `DB_LOCATION` | Where SQLite databases are stored. | `./data`
    | `MERRIAM_WEBSTER_API_KEY` | Merriam Webster API Key obtained in the [API Keys](#api-keys) section. | *not set*
    | `OXFORD_APP_ID` | **optional** - Oxford Dictionary App ID obtained in the [API Keys](#api-keys) section. | *not set*
    | `OXFORD_APP_KEY` | **optional** - Oxford Dictionary App Key obtained in the [API Keys](#api-keys) section. | *not set*
    | `CLIMATE_CELL_API_KEY` | Tomorrow.io API Key obtained in the [API Keys](#api-keys) section. | *not set*
    | `API_SSL` | Set to `true` if you are utilizing SSL for `roboto_api`. You must include `SSL_KEYFILE` and `SSL_CERT_FILE` locations as shown below. | `false`
    | `SSL_CERT_FILE` | **optional** - Location of SSL certificate. | *not set*
    | `SSL_KEYFILE` | **optional** - Location of SSL private key. | *not set*


- To override any of the default environmental variables, create a file called `.env.local`. 
For example, to set `MERRIAM_WEBSTER_API_KEY` and `CLIMATE_CELL_API_KEY` and change `HTTP_SERVER_PORT`:
    - create a filed called `.env.local`:
        ```
        #.env.local

        HTTP_SERVER_PORT=8001
        MERRIAM_WEBSTER_API_KEY=9d1e4882-x649-20f4-34h5-7eole23fe931
        CLIMATE_CELL_API_KEY=gIODELdkqdPDaaLEL1PWOEfQdfAaaeFPq
        ```

- During the [install](#install) steps`.env.defaults` and `.env.local` will be combined to produce one single `.env` file that Docker will utilize.

## Install
- Clone repo and its submodules.
    ```
    git clone --recurse-submodules https://github.com/roboto84/roboto.git
    ```
    ```
    cd roboto
    ```

- Generate a `.env` file based off of defaults and overrides. (**Note:** This command removes existing `.env` file,
  and you must run this command each time you change an environmental variable.)
    ```
    rm -f .env && (cat ".env.defaults" ".env.local") >> .env
    ```
- Run docker compose: build images and start containers.
    ```
    docker compose up
    ```
    or with docker-compose standalone.
    ```
    docker-compose up
    ```
    (To run in detached mode add `-d` to the docker command.)


- Open browser to [localhost:8080](http://localhost:8080) to view **roboto** running with all of its services.

## Commit Conventions
Git commits follow [Conventional Commits](https://www.conventionalcommits.org) message style as explained in detail on their website.

<br/>
<sup>
    <a href="https://www.flaticon.com/free-icons/robot" title="robot icons">
        roboto icon created by Freepik - Flaticon
    </a>
</sup>
