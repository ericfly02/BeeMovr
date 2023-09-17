<br>
<br>

<p align="center">
  <b>
    Source code for
    <a href="https://beemovr.com">Beemovr.com</a>
  </b>
</p>

Google Maps, but for Beekeepers.
Our project seeks to give beekeepers increased information about ideal pollinator conditions near them to improve efficiency and decrease uncertainty about insufficient honey production by using precipitation and temperature models.
We allow beekeepers to see which area or region has the most amount of potential honey yield.

<br>

## Getting Started
[1.](#1-how-to-spin-up-a-developmental-server) How to spin up a development server<br>
[2.](#2-how-to-set-up-a-production-server) How does this work?<br>
[3.](#3-open-source-projects-we-rely-on) Future Roadmap

<br>

## Acknowledgement

Our work would not have been possible without the paper "[The Impact of Precipitation and Temperature on Honey Yield in the United States](https://etd.auburn.edu/bitstream/handle/10415/7108/Hayes%20Grogan.pdf?sequence=2)" (Hayes Kent Grogan, 2020, Auburn University). The paper provided the BeeMovr team with the prediction formula for the relationship between monthly precipitation / maximum temperature / minimum temperature and honey yield, and this is exactly what made our core functionality possible.

<br>

## 1. How to spin up a development server

***How to run***<br>
```bash
git clone https://github.com/ericfly02/BeeMovr.git
cd BeeMovr
docker compose up
```

***How to stop running and clean up***<br>
```bash
docker compose down
```

<br>

## 2. How does this work?

The UI was largely built with Mapbox.
All of the internal API's were built with Flask.
Whenever the user clicks a point in the map, it calls for a function that calculates the honey production prediction value based on the formula given by Hayes Kent Grogan's paper.

<br>

| Stack | Name |
| ------- | ---- |
| **Front-end** | [React](https://react.dev/) + [Mapbox](https://www.mapbox.com/) |
| **Back-end** | [Flask](https://flask.palletsprojects.com/) |
| **Server** | [DigitalOcean](https://cloud.digitalocean.com/) with 1vCPU, 1GB RAM, 25GB SSD  |
| **Containerization** | [Docker](https://www.docker.com/) + [Docker Compose](https://docs.docker.com/compose/) |

<br>

## 3. Future Roadmap

- `Short Term Goal`: Add a drag functionality, where the user can get the honey production prediction value of a rectangle instead of just a single point.
- `Long Term Goal`: Now, we call the Open Meteo API's everytime the user clicks on a something to get the environmental values (precipitation and max/min temps). This will be replaced by a data storage / caching system. Whenever an API is called, the precipitation and max/min temp values will be stored into either Elastic Stack or PostGIS. Flask caching will also prevent duplicate API calls.
- `Long Term Goal`: Create a heatmap of the honey production potential of all areas based on the data stored on the database.

<br>
<br>
<br>
