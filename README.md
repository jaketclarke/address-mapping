# Address Geocoder

Project to build a useful set of information from an address.

## Setup

* create a .env file from .env.template
  * add a key for opencagegeocoding, with the name `OPENCAGE_GEOCODING_API_KEY`
    * add a `GEOSERVER_URL` like <https://geoserver.domainname.com.au/geoserver/workspacename/>
      * NOTE: end the url in a slash, and don't include the type - i.e, wms, ows, etc
* npm install
* npm run dev
