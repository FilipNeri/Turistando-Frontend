<template>
  <div class="bodyRotas">
    <div class="container">
      <label class="titulo"><strong>Roteiro de Viagens</strong> </label>
      <label class="descricao"
        >Essa página é dedicada à exibir a melhor rota para conhecer praias ou
        pontos históricos da cidade de Laguna.</label
      >
    </div>
    <br />
    <router-link  to="/praias">
      <div class="container--opcao">
        <label>Conheça a rota para as melhores praias de Laguna.</label>
        <img
          class="imagem"
          src="https://cdnstatic8.com/viagensecaminhos.com/wp-content/uploads/2011/12/laguna-praia-mar-grosso.jpg"
          alt="Praia do Mar grosso"
        />
      </div>
    </router-link>
    <router-link to="/pontoshistoricos">
      <div class="container--opcao">
        <label
          >Conheça a rota para visitar a todos pontos históricos de
          Laguna.</label
        >
        <img
          class="imagem"
          src="http://www.renascencahotel.com.br/wp-content/uploads/museu.jpg"
          alt="Museu Anita Garibaldi"
        />
      </div>
    </router-link>
  </div>
</template>

<script>
export default {};
</script>

<style scoped>
router-link,a{
    text-decoration: none ;
    color: inherit;
}
router-link:hover,a:hover{
    text-decoration: none ;
    color: inherit;
}
.bodyRotas {
  padding-left: 10vw;
  padding-right: 10vw;
}
.container {
  display: flex;
  flex-direction: column;
}
.titulo {
  font-size: 25px;
}
.descricao {
  max-width: 300px;
}
.imagem {
  width: 150px;
  height: 150px;
  border-radius: 20%;
}
.container--opcao {
  display: flex;
  justify-content: space-between;
  background-color: #d3d3d3;
  border: solid 2px #6059c1;
  border-radius: 20px;
  padding: 15px;
  margin-bottom: 3px;
}
</style>
