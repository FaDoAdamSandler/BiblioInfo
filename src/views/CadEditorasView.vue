<script>
import {v4 as uuidv4} from 'uuid';
export default {
  data() {
    return {
      editoras: [
        { id: "8ae6623d-5462-4774-b5e1-e263c5d2d367", nome: "editora 1", site:"Site 1" },
        { id: "1f659d91-17b5-40da-b5fb-dbffa5664e27", nome: "editora 2",site:"Site 2" },
        { id: "d5a59ada-da1d-47a2-9a6e-e99964df9571", nome: "editora 3" ,site:"Site 3"},
        { id: "2311c938-42fa-4661-a3fc-9ba664a30f6e", nome: "editora 4" ,site:"Site 4" },
        { id: "6f58a76b-0ea0-4bca-8d93-296c7d69685c", nome: "editora 5" ,site:"Site 5" },
      ],
    };
  },
  methods: {
    salvar(){
      if (this.novo_editora !==""){
        const novo_id = uuidv4();
        this.editoras.push({
          id: novo_id,
          nome: this.novo_editora,
          site:this.novo_site,
      });
      this.novo_editora = ""; 
      }
    },
    excluir(editora){
      const indice = this.editoras.indexOf(editora);
      this.editoras.splice(indice, 1);
    }
  },
};
</script>

<template>
  <div class="container">
    <div class="title">
      <h2>Cadastro de editoras</h2>
    </div>
    <div class="form-input">
      <input type="text" placeholder = "Editora:" v-model="novo_editora"/>
      <input type="text" placeholder = "Site" v-model="novo_site"/>
      <button @click="salvar">Salvar</button>
    </div>
    <div class="list-editoras">
      <table>
        <thead>
          <tr>
            <th>ID</th>
            <th>Nome</th>
            <th>Site</th>
            <th>Ações</th>
          </tr>
        </thead>
        <tbody>
          <tr v-for="editora in editoras" :key="editora.id">
            <td>{{ editora.id }}</td>
            <td>{{ editora.nome }}</td>
            <td>{{editora.site}}</td>
            <td>
              
              <button class="acoes" @click="excluir(editora)">Excluir</button>
            </td>
          </tr>
        </tbody>
      </table>
    </div>
  </div>
</template>

<style>
</style>
