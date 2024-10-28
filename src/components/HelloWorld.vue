<template>
<h1>Dados em axios</h1>
<div class="button1">
  <button @click="axiosDados">CLICA LEGAL DOG</button>
</div>
<table class="table">

<tbody>
  <tr v-for="item in items" :key="item.id">
      <td>{{ item.user_id }}</td>
      <td>{{ item.title }}</td>
      <td>{{ item.body }}</td>
  </tr>
</tbody>
</table>
</template>

<script>
import axios from 'axios';

export default {
  name: 'MyComponent',
  props: {
    msg: String
  },
  data() {
    return {
      items: []
    };
  },
  methods: {
    async axiosDados(){
      try{
        const response = await axios.get ('https://gorest.co.in/public/v2/posts');
        this.items = response.data;
        console.log(this.items);
      } catch (error) {
        console.error('Erro ao buscar os dados', error);
      }
    }
  }
}

</script>

<style>

.imagemkkk{
  display: block;
  margin: 0 auto;
  max-width: 100%;
}


h1 {
  text-align: center;
}

.button1 {
  text-align: center;
  margin-bottom: 20px;
}

.imagemkkk{
  max-width: 200px;
  height: auto;
  text-align: center
}

button {
  font-size: 16px;
  padding: 10px 20px;
  margin-bottom: 10px;

}
.button1 {
  margin-bottom: 20px;
}
.table {
  width: 100%;
  border-collapse: collapse;
  margin: 0 auto;
  text-align: center;
}

.table td {
  border: 1px solid #ddd;
  padding: 8px;
  color: black;
}
</style>