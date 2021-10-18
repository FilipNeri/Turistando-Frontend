/* <template>
  <div class="bodyRotas">
    <br />
    <div
      v-for="(estabelecimento, index) of estabelecimentos"
      :key="index + estabelecimento.name"
    >
      <div
        class="titulo"
        @click="abrirClasse($event)"
        :id="index + estabelecimento.name"
      >
        <div style="padding-left:5px">{{ estabelecimento.name }}</div>
        <div class="km">{{ distancias[index] }} km</div>
      </div>

      <div
        v-if="
          classeClicada == index + estabelecimento.name && mostraClasse == true
        "
        @click="goElementos(estabelecimento)"
      >
        <!-- <div class="checkbox">
          
        </div> -->
        <div>
          <div class="lista">
            <div class="imagem">
              <img class="imagem" :src="estabelecimento.photos[0].url" alt="" />
            </div>
            <div>
              <div class="texto">{{ estabelecimento.description }}</div>
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      url: process.env.VUE_APP_API,
      estabelecimentos: {},
      mostraClasse: false,
      classeClicada: {},
      distancias: [],
    };
  },
  methods: {
    fetchApi() {
      fetch(this.url)
        .then((response) => response.json())
        .then((json) => {
          this.filtro(json.data);
        })
        .catch((err) => {
          console.log("error", err);
        });
    },
    filtro(json) {
      this.estabelecimentos = json.filter(estabelecimento=>{
        if(estabelecimento.tipo=="ES"){
          return estabelecimento
        }
      });
      this.geolocalizacao();
    },
    abrirClasse(evento) {
      if (this.classeClicada == evento.target.id) {
        this.mostraClasse = !this.mostraClasse;
      } else {
        this.mostraClasse = true;
        this.classeClicada = evento.target.id;
      }
    },
    goElementos(estabelecimento) {
      var obj = estabelecimento;
      console.log(obj);
      localStorage.setItem("objeto", JSON.stringify({ obj }));
      this.$router.push("/elementos");
    },
    geolocalizacao() {
      if ("geolocation" in navigator) {
          navigator.geolocation.getCurrentPosition(
            (position) => {
              this.estabelecimentos.forEach((ponto) => {
                var distancia = this.getDistanceFromLatLonInKm(
                  {
                    lat: position.coords.latitude,
                    lng: position.coords.longitude,
                  },
                  { lat: ponto.coordinates.lat, lng: ponto.coordinates.lng }
                );

                var d = distancia / 1000;
                d = d.toFixed(1);
                this.distancias.push(d);
              });
            },
            (error) => {
             
              console.log(error);
            }
          
        );
      } else {
        console.log("deu ruim");
      }
    },
    getDistanceFromLatLonInKm(position1, position2) {
      "use strict";
      var deg2rad = function(deg) {
          return deg * (Math.PI / 180);
        },
        R = 6371,
        dLat = deg2rad(position2.lat - position1.lat),
        dLng = deg2rad(position2.lng - position1.lng),
        a =
          Math.sin(dLat / 2) * Math.sin(dLat / 2) +
          Math.cos(deg2rad(position1.lat)) *
            Math.cos(deg2rad(position1.lat)) *
            Math.sin(dLng / 2) *
            Math.sin(dLng / 2),
        c = 2 * Math.atan2(Math.sqrt(a), Math.sqrt(1 - a));
      return (R * c * 1000).toFixed();
    },
  },
  mounted() {
    this.fetchApi();
  },
};
</script>

<style scoped>
.bodyRotas {
  padding-left: 10vw;
  padding-right: 10vw;
}
.titulo {
  display: flex;
  justify-content: space-between;
  align-items: center;
  background-color: #dcdcdc;
  color: #6059c1;
  border: 2px solid #6059c1;
  border-radius: 12px;
  height: 50px;
  font-size: 20px;
  margin-top: 2px;
}
.km {
  font-size: 12px;
  display: flex;
}
.checkbox {
  color: #6059c1;
  margin-left: 20px;
}
.lista {
  list-style: none;
  display: flex;
  padding: 5px;
}
.texto {
  margin-left: 5px;
}
.imagem {
  border-radius: 20%;
  height: 150px;
  width: 150px;
  max-width: 150px;
  max-height: 150px;
}
</style>
 */