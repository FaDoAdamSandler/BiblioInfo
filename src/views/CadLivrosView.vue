<script>
import {v4 as uuidv4} from 'uuid';
export default {
  data() {
    return {
      livros: [
        { id: "8ae6623d-5462-4774-b5e1-e263c5d2d367", nome: "Livro 1", quantidade:"Quantidade 1", preco:"Preço 1" , Editora:"Editora 1", Categoria:"Categoria 1"},
        { id: "1f659d91-17b5-40da-b5fb-dbffa5664e27", nome: "Livro 2", quantidade:"Quantidade 2", preco:"Preço 2" , Editora:"Editora 2", Categoria:"Categoria 2"},
        { id: "d5a59ada-da1d-47a2-9a6e-e99964df9571", nome: "Livro 3", quantidade:"Quantidade 3", preco:"Preço 3", Editora:"Editora 3", Categoria:"Categoria 3" },
        { id: "2311c938-42fa-4661-a3fc-9ba664a30f6e", nome: "Livro 4", quantidade:"Quantidade 4", preco:"Preço 4", Editora:"Editora 4", Categoria:"Categoria 4"},
        { id: "6f58a76b-0ea0-4bca-8d93-296c7d69685c", nome: "Livro 5" , quantidade:"Quantidade 5", preco:"Preço 5", Editora:"Editora 5", Categoria:"Categoria 5"},
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
          quantidade:this.nova_quantidade,
          preco:this.novo_preco,
          Editora:this.nova_editora
          
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
      <input type="text" placeholder="Nome do livro:" v-model="novo_livro"/>
      <input type="text" placeholder="Quantidade de modelos:" v-model="nova_quantidade"/>
      <input type="text" placeholder="Preço:" v-model="novo_preco"/>
      <select name="Editoras" class="editora" v-model = "nova_editora">
  <option value="Editora1">Editora 1</option>
  <option value="Editora2">Editora 2</option>
  <option value="Editora3">Editora 3</option>
  <option value="Editora4">Editora 4</option>
  <option value="Editora5">Editora 5</option>
  </select>
  <select name="Categorias" class="categoria">
  <option Categoria="Categoria1">Categoria 1</option>
  <option Categoria="Categoria2">Categoria 2</option>
  <option Categoria="Categoria3">Categoria 3</option>
    <option Categoria="Categoria4">Categoria 4</option>
      <option Categoria="Categoria5">Categoria 5</option>
</select>
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-livros">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Quantidade</th>
            <th>Preço</th>
            <th>Editora</th>
            <th>Categoria</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="livro in livros" :key="livro.id">
            <td>{{ livro.id }}</td>
            <td>{{ livro.nome }}</td>
            <td>{{livro.quantidade}}</td>
            <td>{{livro.preco}}</td>
            <td>{{livro.Editora}}</td>
            <td>{{livro.Categoria}}</td>
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
