# electricitymap [![Slack Status](http://slack.tmrow.co/badge.svg)](http://slack.tmrow.co)
 
A real-time visualisation of the GHG and CO2 footprint of electricity generation built with [d3.js](https://d3js.org/), optimized for Google Chrome. Try it out at [http://electricitymap.tmrow.co](http://electricitymap.tmrow.co).


![image](https://cloud.githubusercontent.com/assets/1655848/20340757/5ada5cf6-abe3-11e6-97c4-e68929b8a135.png)

Consider [contributing](#contribute) or submit ideas, feature requests or bugs on the [issues](https://github.com/corradio/electricitymap/issues) page.

test

## Data sources

### GreenHouse Gas footprint calcuation and data source
The GreenHouse Gas (GHG) footprint of each country is measured from the perspective of a consumer. It represents the GHG footprint of 1 kWh consumed inside a given country, in the gCO2eq unit (meaning each GHG is converted to its CO2 equivalent in terms of global warming potential). 

The GHG footprint of each production mode takes into account the construction of production units and their usual lifetimes as calculated by the 2014 IPCC report (see [wikipedia entry](https://en.wikipedia.org/wiki/Life-cycle_greenhouse-gas_emissions_of_energy_sources#2014_IPCC.2C_Global_warming_potential_of_selected_electricity_sources) and [co2eq.js#L1](https://github.com/corradio/electricitymap/blob/master/api/static/app/co2eq.js#L1)).

Each country has a GHG mass flow that depends on neighboring countries. In order to determine the GHG footprint of each country, the set of coupled GHG mass flow balance equations of each countries must be solved simultaneously. This is done by solving the linear system of equations defining the network of GHG exchanges (see [co2eq.js#L52](https://github.com/corradio/electricitymap/blob/master/api/static/app/co2eq.js#L52)).


### Real-time electricity data sources
- Austria: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Belgium: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Bulgaria: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Czech Republic: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Denmark: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Estonia: [energinet.dk](http://www.energinet.dk/EN/El/Sider/Det-nordiske-elsystem.aspx)
- Finland: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- France: [RTE](http://www.rte-france.com/en/eco2mix/eco2mix-mix-energetique-en)
- Germany: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Great Britain: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Greece: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Hungary: [Mavir](http://www.mavir.hu/web/mavir-en/actual-generation-per-production-type-net-operation-control-measurement)
- Ireland: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Italy: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Latvia: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Lithuania: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Norway: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Poland: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Portugal: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Romania: [Transelectrica](http://www.transelectrica.ro/en/web/tel/home)
- Slovakia: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Slovenia: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Spain: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Sweden: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)
- Switzerland: [ENTSOE](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html)

### Production capacity data sources
- Austria: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Belgium: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Bulgaria: [wikipedia.org](https://en.wikipedia.org/wiki/Energy_in_Bulgaria)
- Czech Republic: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Denmark
  - Solar: [wikipedia.org](https://en.wikipedia.org/wiki/Solar_power_in_Denmark)
  - Wind: [wikipedia.org](https://en.wikipedia.org/wiki/Wind_power_in_Denmark#Capacities_and_production)
  - Other: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Estonia: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Finland
  - Hydro: [worldenergy.org](https://www.worldenergy.org/data/resources/country/finland/hydropower/)
  - Nuclear: [iaea.org](http://www-pub.iaea.org/MTCD/Publications/PDF/CNPP2013_CD/countryprofiles/Finland/Finland.htm)
  - Wind: [EWEA](http://www.ewea.org/fileadmin/files/library/publications/statistics/EWEA-Annual-Statistics-2015.pdf)
- France
  - Solar: [wikipedia.org](https://en.wikipedia.org/wiki/Solar_power_by_country)
  - Wind: [EWEA](http://www.ewea.org/fileadmin/files/library/publications/statistics/EWEA-Annual-Statistics-2015.pdf)
  - Other: [RTE](http://clients.rte-france.com/lang/an/visiteurs/vie/prod/parc_reference.jsp)
- Germany: 
  - [Fraunhofer ISE](https://www.energy-charts.de/power_inst.htm)
  - [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Great Britain
  - Gas: [energy-uk.org.uk](http://www.energy-uk.org.uk/energy-industry/gas-generation.html)
  - Hydro: [wikipedia.org](https://en.wikipedia.org/wiki/Hydroelectricity_in_the_United_Kingdom)
  - Nuclear: [wikipedia.org](https://en.wikipedia.org/wiki/Nuclear_power_in_the_United_Kingdom)
  - Solar: [wikipedia.org](https://en.wikipedia.org/wiki/Solar_power_by_country)
  - Wind: [wikipedia.org](https://en.wikipedia.org/wiki/Wind_power_in_the_United_Kingdom)
- Greece: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Hungary: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Ireland: 
  - All production types [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
  - Wind: [IWEA](http://www.iwea.com/index.cfm/page/windenergyfaqs?#q21)
- Italy
  - Hydro: [wikipedia.org](https://en.wikipedia.org/wiki/Electricity_sector_in_Italy)
  - Nuclear: [wikipedia.org](https://en.wikipedia.org/wiki/Electricity_sector_in_Italy)
  - Solar: [wikipedia.org](https://en.wikipedia.org/wiki/Electricity_sector_in_Italy)
  - Wind: [wikipedia.org](https://en.wikipedia.org/wiki/Electricity_sector_in_Italy)
- Latvia: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Lithuania: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Netherlands: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Norway
  - Gas: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
  - Hydro: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
  - Wind: [ieawind.org](http://www.ieawind.org/countries/norway.html)  
- Poland: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Portugal: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Romania: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Slovenia: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)
- Spain: [ree.es](http://www.ree.es/sites/default/files/downloadable/preliminary_report_2014.pdf)
- Sweden
  - Hydro: [worldenergy.org](https://www.worldenergy.org/data/resources/country/sweden/hydropower/)
  - Nuclear: [world-nuclear.org](http://www.world-nuclear.org/information-library/country-profiles/countries-o-s/sweden.aspx)
  - Solar: [wikipedia.org](https://en.wikipedia.org/wiki/Energy_in_Sweden)
  - Wind: [EWEA](http://www.ewea.org/fileadmin/files/library/publications/statistics/EWEA-Annual-Statistics-2015.pdf)
- Switzerland: [ENTSO-E](https://transparency.entsoe.eu/generation/r2/installedGenerationCapacityAggregation/show)


### Real-time weather data sources
We use the [US National Weather Service's Global Forecast System (GFS)](http://nomads.ncep.noaa.gov/)'s GFS 0.25 Degree Hourly data.
Forecasts are made every 6 hours, with a 1 hour time step.
The values extracted are wind speed and direction at 10m altitude, and ground solar irradiance (DSWRF - Downward Short-Wave Radiation Flux), which takes into account cloud coverage.
In order to obtain an estimate of those values at current time, an interpolation is made between two forecasts (the one at the beginning of the hour, and the one at the end of the hour).


### Topology data
We use the [Natural Earth Data Cultural Vectors](http://www.naturalearthdata.com/downloads/10m-cultural-vectors/) country boundaries.


## Contribute
Want to help? Join us on slack at [http://slack.tmrow.co](http://slack.tmrow.co).
In the meantime, here's some things you can do:
- check out the [issues](https://github.com/corradio/electricitymap/issues)
- add your country by writing a [parser](https://github.com/corradio/electricitymap/tree/master/feeder/parsers)
- update an existing [parser](https://github.com/corradio/electricitymap/tree/master/feeder/parsers) with a different API if you know one with more data or closer to real-time
- optimise the code, correct inaccuracies...

You can also see a list of missing informations displayed as warnings in the developer console, or question marks in the country panel:

![image](https://cloud.githubusercontent.com/assets/1655848/16256617/9c5872fc-3853-11e6-8c84-f562679086f3.png)

To get started, clone or [fork](https://help.github.com/articles/fork-a-repo/) the repository, and install [Docker](https://docs.docker.com/engine/installation/). then you just run `docker-compose up`. Head over to [http://localhost:8000/](http://localhost:8000/) and you should see the map!

You can then start editing the code. If you edit the frontend it will need compiling. You should run
```
docker-compose run web npm run watch
```
in order to compile your modifications on the fly.

Once you're done doing your changes, submit a [pull request](https://help.github.com/articles/using-pull-requests/) to get them integrated.

## Troubleshooting

- `ERROR: Couldn't find env file:` env files are used to store sensitive information such as API keys. If you get this error after running `docker-compose up`, create an empty file named `secrets.env` in the root folder

- `KeyError: 'ENTSOE_TOKEN'`: in order to request data from the ENTSOE, you need an API key. You can create an account and request your API key by [following this link](https://transparency.entsoe.eu/content/static_content/Static%20content/web%20api/Guide.html). Once you have it, add it to your `secrets.env` file. 
