<script>
import {v4 as uuidv4} from 'uuid';
export default {
  data() {
    return {
      livros: [
        { id: "8ae6623d-5462-4774-b5e1-e263c5d2d367", nome: "livro 1" },
        { id: "1f659d91-17b5-40da-b5fb-dbffa5664e27", nome: "livro 2" },
        { id: "d5a59ada-da1d-47a2-9a6e-e99964df9571", nome: "livro 3" },
        { id: "2311c938-42fa-4661-a3fc-9ba664a30f6e", nome: "livro 4" },
        { id: "6f58a76b-0ea0-4bca-8d93-296c7d69685c", nome: "livro 5" },
      ],
    };
  },
  methods: {
    salvar(){
      if (this.novo_livro !==""){
        const novo_id = uuidv4();
        this.livros.push({
          id: novo_id,
          nome: this.novo_livro,
      });
      this.novo_livro = ""; 
      }
    },
    excluir(livro){
      const indice = this.livros.indexOf(livro);
      this.livros.splice(indice, 1);
    }
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Cadastro de livros</h2>
    </div>
    <div class="form-input">
      <input type="text" v-model="novo_livro"/>
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-livros">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="livro in livros" :key="livro.id">
            <td>{{ livro.id }}</td>
            <td>{{ livro.nome }}</td>
            <td>
              
              <button class="acoes" @click="excluir(livro)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style>
</style>
