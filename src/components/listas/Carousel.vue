<template>
<div>
  
  <div @click="goElementos($event)">
    <b-carousel
        
        id="carousel-fade"
        style="text-shadow: 0px 0px 2px #000"
        fade
        img-width="1024"
        img-height="480"

      >
        <b-carousel-slide v-for="(item,index) of items "
          caption=""
          :img-src="item.photos[0].url"
          :img-alt="item.name"
          :key="index"
          :id="item.id"
          img-width="1024"
          img-height="480"
          class="imagem"
        >
        </b-carousel-slide>
        
        </b-carousel>
        
    </div>
</div>
</template>

<script>
export default {
  data() {
    return {
      items: [],
      url: process.env.VUE_APP_API,

    };
  },
  methods: {
    goElementos(id){
      var i = this.items.filter(item=>{
        if(item.id == id.path[1].id){
          return item
        }
      })
      i=i[0]
      var obj = i;
      //console.log(obj)
      localStorage.setItem(
        "objeto",
        JSON.stringify({obj} )
      );
      this.$router.push('/elementos')
    },
    fetchApi() {
      fetch(this.url)
        .then((response) => response.json())
        .then((json) => {
          json.data = json.data.filter(item=>{
            if(item.photos.length!=0 && item.tipo=="EV"){
              //console.log(item.photos.length)
              return item
            }
          })
          this.items = json.data;
          console.log(this.items);
        })
        .catch((err) => {
          console.log("error", err);
        });
    },
  },
  mounted() {
  this.fetchApi()
  },
};
</script>

<style scoped>
.imagem{
  max-width: 1024px;
  max-height: 480px;

}
</style>