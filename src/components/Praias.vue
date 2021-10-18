<template>
  <div class="bodyRotas">
    <br />
    <!--    <div class="circulo">
          <div class="retangulo"></div>
    </div> -->
    <div class="container--opcao">
      <div
        style="display:flex; justify-content:space-between; flex-direction:column;"
      >
        <label>Conheça a rota para as melhores praias de Laguna.</label>
        <strong> Endereço</strong>
      </div>
      <img
        class="imagem"
        src="https://cdnstatic8.com/viagensecaminhos.com/wp-content/uploads/2011/12/laguna-praia-mar-grosso.jpg"
        alt="Praia do Mar grosso"
      />
    </div>
  </div>
</template>

<script>
export default {};
</script>

<style>
.bodyRotas {
  padding-left: 10vw;
  padding-right: 10vw;
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
.imagem {
  width: 150px;
  height: 150px;
  border-radius: 20%;
}
.circulo {
  height: 60px;
  width: 60px;
  background-color: #6059c1;
  border: solid 2px #fff;
  border-radius: 50%;
  display: flex;
  align-items: flex-start;
  justify-content: center;
  box-shadow: 0 0 0 0.2em black;
}
.retangulo {
  position: relative;
  top: 55px;
  border: solid 2px #fff;
  border-top: none;
  border-bottom: none;
  height: 100px;
  width: 20px;
  background-color: #6059c1;
  box-shadow: 0.2em 0 0 0 black;
}
</style>
