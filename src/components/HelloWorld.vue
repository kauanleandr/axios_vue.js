<template>
<h1>Dados em axios</h1>

<div class="button1">
  <button @click="axiosDados">CARREGAR DADOS</button>
</div>

<div class="button1">
  <button @click="axiosAdicionar">ADICIONAR DADOS</button>
</div>

<div class="button1">
  <button @click="axiosFechar">FECHAR DADOS</button>
</div>

<table class="table">

<tbody>
  <tr v-for="item in items" :key="item.id">
      <td>{{ item.id }}</td>
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

    async axiosAdicionar(){
      try {
    const response = await axios.post('https://jsonplaceholder.typicode.com/posts', {
      id: '',
      user_id: '21324',
      title: 'quaerat velit veniam amet cupiditate aut numquam ut sequi, consequuntur deleniti eos quia temporibus ab aliquid at',
      body: 'voluptatem cumque tenetur consequatur expedita ipsum nemo quia explicabo aut eum minima consequatur tempore cumque quae est et et in consequuntur voluptatem voluptates aut, odit qui et et necessitatibus sint veniam mollitia amet doloremque molestiae commodi similique magnam et quam blanditiis est itaque quo et tenetur ratione occaecati molestiae tempora',
    }, {
      headers: {
        'Content-Type': 'application/json',
        'Authorization': 'Bearer SEU_TOKEN_AQUI' 
      }
    });
        const newItem = response.data;
        this.items.push(newItem);
        console.log('atualizando dados', this.items);
      } catch(error) {
        console.error('erro ao carregar dados', error)
      }
    },

    async axiosDados(){
      try{
        const response = await axios.get ('https://jsonplaceholder.typicode.com/posts');
        this.items = response.data;
        console.log(this.items);
      } catch (error) {
        console.error('Erro ao buscar os dados', error);
      }
    },
    axiosFechar(){
      this.items = [];
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