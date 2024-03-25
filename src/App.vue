<script setup>
import { ref, reactive } from 'vue'

const name = ref('')
const age = ref('')
const produto = reactive({
  nome: '',
  preco: 0,
  estoque: '',
  categorias: []
})
const ver = ref(false)
</script>

<template>
  <dvi class="container">
    <div class="formulario">
      <h1>Formulario</h1>
      <form>
        <label for="name">Nome</label>
        <input type="text" id="name" name="name" v-model="produto.nome" /><br />
        <label for="age">Preco</label>
        <input type="number" id="age" name="age" v-model="produto.preco" /><br />
        <label for="estoque">Estoque</label>
        <input type="number" id="estoque" name="estoque" v-model="produto.estoque" /><br />
        <label for="categorias">Categorias</label>
        <select multiple id="categorias" name="categorias" v-model="produto.categorias">
          <option value="eletronicos">Eletronicos</option>
          <option value="moveis">Moveis</option>
          <option value="roupas">Roupas</option>
          <option value="alimentos">Alimentos</option>

          <option value="bebidas">Bebidas</option>
          <option value="refrigeracao">Refrigeracao</option>
          <option value="limpeza">Limpeza</option>
          <option value="higiene">Higiene</option>
          <option value="beleza">Beleza</option></select
        ><br />
        <button type="button" @click="ver = !ver">Ver</button>
      </form>
    </div>
    <Transition name="fade">
      <div class="resultado" v-if="ver">
        <h1>Resultado:</h1>
        <div>
          <p>{{ name }}</p>
          <p>{{ age }}</p>
          <h2>O produto</h2>
          <h3>dados do produto</h3>
          <p>Nome: {{ produto.nome }}</p>
          <p>R$ {{ produto.preco.toFixed(2).replace(',', '.') }}</p>
          <p>Estoque: {{ produto.estoque }}</p>
          <p>Categorias: {{ produto.categorias }}</p>
        </div>
      </div>
    </Transition>
  </dvi>
</template>

<style scoped>
.container {
  display: flex;
  flex-direction: row;
  column-gap: 2rem;
}
.formulario,
.resultado {
  min-height: 80vw;
  width: 48vw;
  border-radius: 10px;
  padding: 10px;
  margin-top: 2%;
}
.formulario {
  background-color: azure;
}
.resultado {
  background-color: bisque;
}
.v-enter-active,
.v-leave-active {
  transition: opacity 0.5s;
}
.v-enter-active {
  opacity: 0;
}
.v-leave-active {
  opacity: 1;
}
</style>
