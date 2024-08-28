# Address Mapping

Project to use a [Leaflet Map](https://leafletjs.com/) to explore administrative for Australian addresses. This is deployed [here](https://address-mapping.jakeclarke.au/).

This project assumes you have a [Geoserver](https://geoserver.org/) set up. If not, I also have a repo explaining how to get a Geoserver install with working HTTPS going in a [Docker](https://www.docker.com/) container up here [geoserver-https](https://github.com/jaketclarke/geoserver-https/).

It also assumes you have set up the layers invoked by the Leaflet Map in the [index.ejs](https://github.com/jaketclarke/address-mapping/blob/main/views/index.ejs) file.

So for example:

```js
  // get fed elec
  layer = 'electorates:Federal Electorates Current';
  var wfsUrl = buildWfsQueryUrl(latLng, layer)
  var properties = await fetchPropertiesFromWFS(wfsUrl)
  federalElec = properties && properties['elecName'] ? titleCase(properties['elecName']) : 'Not Found';

```

This code assumes there is a layer called 'Federal Electorates Current', in a workspace called 'electorates', which has a name property in a field called 'elecName'.

This code also uses [OpenCage](https://opencagedata.com/) for address geocoding. To run it you will need to set up an OpenCage account.

## Development

This assumes a linux development environment, and that you have already [installed NPM](https://www.digitalocean.com/community/tutorials/how-to-install-node-js-on-ubuntu-22-04). E.g,

* create a `.env` file from [.env.template](https://github.com/jaketclarke/address-mapping/blob/main/.env.template)
  * add a key for opencagegeocoding, with the name `OPENCAGE_GEOCODING_API_KEY`
    * add a `GEOSERVER_URL` like <https://geoserver.domainname.com.au/geoserver/workspacename/>
      * NOTE: end the url in a slash, and don't include the type - i.e, wms, ows, etc
* `npm install`
* `npm run dev`
