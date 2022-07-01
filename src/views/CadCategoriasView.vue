<script>
import {v4 as uuidv4} from 'uuid';
export default {
  data() {
    return {
      Categorias: [
        { id: "8ae6623d-5462-4774-b5e1-e263c5d2d367", nome: "Categoria 1", descricao: "Descrição 1" },
        { id: "1f659d91-17b5-40da-b5fb-dbffa5664e27", nome: "Categoria 2" , descricao: "Descrição 2"},
        { id: "d5a59ada-da1d-47a2-9a6e-e99964df9571", nome: "Categoria 3", descricao: "Descrição 3" },
        { id: "2311c938-42fa-4661-a3fc-9ba664a30f6e", nome: "Categoria 4" , descricao: "Descrição 4"},
        { id: "6f58a76b-0ea0-4bca-8d93-296c7d69685c", nome: "Categoria 5" , descricao: "Descrição 5"},
      ],
    };
  },
  methods: {
    salvar(){
      if (this.novo_Categoria !==""){
        const novo_id = uuidv4();
        this.Categorias.push({
          id: novo_id,
          nome: this.novo_Categoria,
          descricao: this.nova_descricao
      });
      this.novo_Categoria = ""; 
      }
    },
    excluir(Categoria){
      const indice = this.Categorias.indexOf(Categoria);
      this.Categorias.splice(indice, 1);
    }
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Cadastro de Categorias</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder="Categoria:" v-model="novo_Categoria"/>
      <input type="text" placeholder="Descrição:" v-model="nova_descricao"/>
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-Categorias">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Descrição</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="Categoria in Categorias" :key="Categoria.id">
            <td>{{ Categoria.id }}</td>
            <td>{{ Categoria.nome }}</td>
            <td>{{Categoria.descricao}}</td>
            <td>
              <button class="acoes" @click="excluir(Categoria)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style>
</style>