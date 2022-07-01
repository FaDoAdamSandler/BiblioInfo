<script>
import {v4 as uuidv4} from 'uuid';
export default {
  data() {
    return {
      autores: [
        { id: "8ae6623d-5462-4774-b5e1-e263c5d2d367", nome: "Autor 1", livros:"Livro 1" },
        { id: "1f659d91-17b5-40da-b5fb-dbffa5664e27", nome: "Autor 2", livros:"Livro 2"},
        { id: "d5a59ada-da1d-47a2-9a6e-e99964df9571", nome: "Autor 3" , livros:"Livro 3"},
        { id: "2311c938-42fa-4661-a3fc-9ba664a30f6e", nome: "Autor 4", livros:"Livro 4" },
        { id: "6f58a76b-0ea0-4bca-8d93-296c7d69685c", nome: "Autor 5", livros:"Livro 5" },
      ],
    };
  },
  methods: {
    salvar(){
      if (this.novo_autor !==""){
        const novo_id = uuidv4();
        this.autores.push({
          id: novo_id,
          nome: this.novo_autor,
          livros:this.novo_livro
      });
      this.novo_autor = ""; 
      }
    },
    excluir(autor){
      const indice = this.autores.indexOf(autor);
      this.autores.splice(indice, 1);
    }
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Cadastro de autores</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder="Autor:" v-model="novo_autor"/>
      <input type="text" placeholder= "Livros:" v-model="novo_livro"/>
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-autores">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Livros</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="autor in autores" :key="autor.id">
            <td>{{ autor.id }}</td>
            <td>{{ autor.nome }}</td>
            <td>{{autor.livros}}</td>
            <td>
              
              <button class="acoes" @click="excluir(autor)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style>
</style>
