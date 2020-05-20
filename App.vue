<template>
  <div>
    <l-map :zoom="zoom" :center="center" style="height: 500px; width: 100%;">
      <l-tile-layer :url="url" :attribution="attribution"/>

      <!-- OFFICES -->
      <l-marker
        v-for="office in offices"
        :key="office.id"
        :lat-lng="office.latlng"
        @l-add="$event.target.openPopup()"
        :icon="office_icon"
      >
        <l-popup :content="office.content"></l-popup>
      </l-marker>

      <!-- FACTORIES -->
      <l-marker
        v-for="factory in factories"
        :key="factory.id"
        :lat-lng="factory.latlng"
        @l-add="$event.target.openPopup()"
        :icon="factory_icon"
      >
        <l-popup :content="factory.content"></l-popup>
      </l-marker>

      <!-- WAREHOUSES -->
      <l-marker
        v-for="warehouse in warehouses"
        :key="warehouse.id"
        :lat-lng="warehouse.latlng"
        @l-add="$event.target.openPopup()"
        :icon="warehouse_icon"
      >
        <l-popup :content="warehouse.content"></l-popup>
      </l-marker>
    </l-map>
  </div>
</template>


<script>
import { LMap, LTileLayer, LMarker, LIcon, LPopup } from "vue2-leaflet";
import { latLng, icon } from "leaflet";

export default {
  name: "Icon",
  components: {
    LMap,
    LTileLayer,
    LMarker,
    LIcon,
    LPopup
  },
  data() {
    return {
      zoom: 5,
      center: latLng(47.41322, -1.219482),
      url: "https://{s}.tile.openstreetmap.org/{z}/{x}/{y}.png",
      attribution:
        '&copy; <a href="http://osm.org/copyright">OpenStreetMap</a> contributors',

      //OFFICES
      office_icon: icon({
        iconUrl: "https://image.flaticon.com/icons/svg/717/717940.svg",
        iconSize: [32, 37],
        iconAnchor: [16, 37]
      }),
      offices: [
        {
          id: 1,
          latlng: latLng(55.56197, 12.97629),
          content: `<img src=''>Sweden Office`
        },
        {
          id: 2,
          latlng: latLng(55.6694, 12.568525),
          content: `<img src=''>Bernstorffsgade 50, 1577 Copenhagen`
        },
        {
          id: 3,
          latlng: latLng(52.30136, 4.86619),
          content: `<img src=''>Netherland office`
        },
        {
          id: 4,
          latlng: latLng(50.87308, 4.28677),
          content: `<img src=''>End market office, Belgium`
        },
        {
          id: 5,
          latlng: latLng(50.84186, 4.37323),
          content: `<img src=''>EU office, Belgium`
        },
        {
          id: 6,
          latlng: latLng(51.49664, -0.27428),
          content: `<h1>UK office</h1>
<p><strong>Employees</strong>&nbsp;</p>
<p>Office Members: 166</p>
<p>TMRs AM: 107</p>
<p><strong>Previous incidents:</strong></p>
<ul>
    <li>Assault</li>
    <li>Robbery</li>
    <li>Info sec issue</li>
    <li>Ecommerce Fraud</li>
    <li>Financial Fraud</li>
    <li>Supply Chain issue: Truck break in</li>
    <li>Racial harassment</li>
    <li>Sexual harassment</li>
    <li>Rape</li>
</ul>
          
          <img src='https://lh5.googleusercontent.com/p/AF1QipPpA-BQA9xeXV850OAl1tciQNtGWGwO8tkkFLbO=w426-h240-k-no'>
          
          NWEA & End Market, UK`
        },
        {
          id: 7,
          latlng: latLng(53.59827, -2.29314),
          content: `<img src=''>Retail office, UK`
        },
        {
          id: 8,
          latlng: latLng(53.27677, -6.21794),
          content: `<img src=''>Apex building, Ireland`
        },
        {
          id: 9,
          latlng: latLng(60.16403, 24.91345),
          content: `<img src='https://lh5.googleusercontent.com/p/AF1QipPlPkBEURJGMeZt3_ZFd3I_OtHlP7uCEUO3UVgG=s659-k-no'>Itamerentori 2, Helsinki`
        },
        {
          id: 10,
          latlng: latLng(59.90746, 10.76211),
          content: `<img src='https://geo2.ggpht.com/cbk?panoid=sn24YIoVopQvd7QuK8JlrQ&output=thumbnail&cb_client=search.gws-prod.gps&thumb=2&w=408&h=240&yaw=24.490038&pitch=0&thumbfov=100'>Dronning Eufemias 42, Oslo, Norway`
        },
        {
          id: 11,
          latlng: latLng(48.89079, 2.24424),
          content: `<img src='https://lh5.googleusercontent.com/p/AF1QipMUipvzM4pZwiGuFdoqFQu8UVjoxz8I3g0kb-64=w408-h544-k-no' alt='Cœur Défense'>
          Cœur Défense, 100 Esplanade du Général de Gaulle, Courbevoie, France`
        }
      ],

      // WAREHOUSES
      warehouse_icon: icon({
        iconUrl: "https://image.flaticon.com/icons/svg/2897/2897808.svg",
        iconSize: [32, 37],
        iconAnchor: [16, 37]
      }),
      warehouses: [
        {
          id: 1,
          latlng: latLng(55.883668, 9.776806),
          content: `<img src='https://geo0.ggpht.com/cbk?panoid=RyzhVkKegs1sTkCzT8cuAw&output=thumbnail&cb_client=search.gws-prod.gps&thumb=2&w=408&h=240&yaw=87.38428&pitch=0&thumbfov=100'>Nokiavej 7, Horsens, Denmark`
        },
        {
          id: 2,
          latlng: latLng(55.919466, 9.831342),
          content: `<img src='https://geo3.ggpht.com/cbk?panoid=-aFSuh9MJqiUQ0pZK9DdXA&output=thumbnail&cb_client=search.gws-prod.gps&thumb=2&w=408&h=240&yaw=189.68628&pitch=0&thumbfov=100'>Egeskovvej 7, Horsens, Denmark`
        },
        {
          id: 3,
          latlng: latLng(55.8783, 12.8719),
          content: `<img src='https://lh5.googleusercontent.com/p/AF1QipPtBAJf8_JOC5exd6M2LkF6Jg2vzLdpxHIelYRK=w408-h306-k-no'>DSV Air & Sea AB, Österleden 201, Landskrona, Sweden`
        },
        {
          id: 4,
          latlng: latLng(60.31864, 24.904),
          content: `<img src='https://lh5.googleusercontent.com/p/AF1QipOtMOnUEZJkk2xz5Gu_J6RRyh41kIvqTghilIFY=w408-h306-k-no'>DHL Katriinantie 14-16, 01740 Vantaa, Finland`
        },
        {
          id: 5,
          latlng: latLng(60.55269, 27.16314),
          content: `<img src='https://lh5.googleusercontent.com/p/AF1QipPZJVHQbMO4X67-oUUpidfL7KwdjolmvALRGHG9=w408-h544-k-no'>DHL Syväsatamantie 10, 49460 Hamina, Finland`
        },
        {
          id: 6,
          latlng: latLng(59.5738, 10.74725),
          content: `<img src='https://geo2.ggpht.com/cbk?panoid=hKa9i9uLOtxH6c-rIIlvbQ&output=thumbnail&cb_client=search.gws-prod.gps&thumb=2&w=408&h=240&yaw=5.153171&pitch=0&thumbfov=100'>Toveien 28, 1540 Vestby, Norway`
        },
        {
          id: 7, //IMAGE NOT AVAILABLE
          latlng: latLng(51.33151, 5.9159),
          content: `<img src=''>DHL Zwenkgras 9, 5986 PM Beringe, Holland`
        },
        {
          id: 8,
          latlng: latLng(51.67399, 4.59079),
          content: `<img src='https://lh5.googleusercontent.com/p/AF1QipOlLHVE3DWtaY6aicL33CeWLuVFWHQqtBhK_rWg=w408-h306-k-no'>DSV Orionweg 9, 4782 SC Moerdijk, Holland`
        },
        {
          id: 9, //IMAGE NOT AVAILABLE
          latlng: latLng(53.2086, 6.5394),
          content: `<img src=''>BAT Warehouse, Peizerweg, Groningen, Holland`
        },
        {
          id: 10,
          latlng: latLng(51.10136, 4.3175),
          content: `<img src='https://lh5.googleusercontent.com/p/AF1QipN3zq7nRTFmsdcQQWVz16NUMyLiUSZaI_yj4Tuz=w426-h240-k-no'>DHL Bornem, Oude sluisweg 32, 2880 Bornem, Belgien`
        },
        {
          id: 11,
          latlng: latLng(53.43093, -1.23894),
          content: `<img src='https://lh5.googleusercontent.com/p/AF1QipNoCmsFK21xyQmZNDccJuRcPLf1rLOB4Yf20Ro4=w408-h791-k-no'>Clipper Logistics, Hellaby Ln, Bramley, Rotherham S66 8HN, England`
        },
        {
          id: 12,
          latlng: latLng(53.32508, -6.37157),
          content: `<img src='https://lh5.googleusercontent.com/p/AF1QipOmH1-SgpdsHhtp6YWgSbVouLwEQWqIBGHzJBBo=w426-h240-k-no'>DHL Western Business Park, Dublin, Irland`
        }
      ],

      // FACTORIES
      factory_icon: icon({
        iconUrl: "https://image.flaticon.com/icons/svg/1037/1037503.svg",
        iconSize: [32, 37],
        iconAnchor: [16, 37]
      }),
      factories: [
        {
          id: 1, //IMAGE NOT AVAILABLE
          latlng: latLng(57.84239, 13.29147),
          content: `<img src=''>Winnigton AB, Stationsvägen 11, 52374 Höckerum, Sweden`
        },
        {
          id: 2,
          latlng: latLng(55.55403, 13.06179),
          content: `<img src='https://geo1.ggpht.com/cbk?panoid=BeARfJTwVkk-d9qM1cbFYQ&output=thumbnail&cb_client=search.gws-prod.gps&thumb=2&w=408&h=240&yaw=95.90961&pitch=0&thumbfov=100'><img src=''>Fiedler & Lundgren AB, Stenåldersgatan 23, 21376 Malmö, Sweden`
        },
        {
          id: 3,
          latlng: latLng(53.21144, 6.55562),
          content: `<img src='https://geo3.ggpht.com/cbk?panoid=nxmjOeoosxw7m3VdebJViw&output=thumbnail&cb_client=search.gws-prod.gps&thumb=2&w=408&h=240&yaw=285.99237&pitch=0&thumbfov=100'>
          British American Tobacco Niemeyer B.V., Paterswoldseweg 43, Groningen, Holland`
        }
      ]
    };
  }
};
</script>

<style>
.someExtraClass {
  background-color: aqua;
  padding: 10px;
  border: 1px solid #333;
  border-radius: 0 20px 20px 20px;
  box-shadow: 5px 3px 10px rgba(0, 0, 0, 0.2);
  text-align: center;
  width: auto !important;
  height: auto !important;
  margin: 0 !important;
}

.leaflet-container a.leaflet-popup-close-button {
  display: none;
}

.leaflet-popup-content img {
  height: 400px;
  width: 100%;
  object-fit: contain;
}
</style>
