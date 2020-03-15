<template>
  <div>
    <h5>{{title}} <span class="badge badge-info">{{ items.length }}</span></h5> <!-- Mostra a qtde de itens -->
    <div class="card">
      <div class="card-body">
        <ul class="list-group"> <!-- Lista -->
          <li class="list-group-item" v-for="item in items" v-bind:key="item"> <!-- itens da lista -->
            <div class="row">
              <div class="col-md">
                {{ item }} <!-- renderiza os itens dinâmicamente com o objeto "items" -->
              </div>
              <div class="col-md text-right">
                <button class="btn btn-info" v-on:click="deleteItem(item)"><span class="fa fa-trash"></span></button>
              </div>
            </div> <!-- fim linha -->
          </li>
          <br/>
          <div class="input-group">  <!-- grupo para o input e o botão ficarem juntos -->
            <input class="form-control" type="text" v-model="item" v-on:keyup.enter="addItem(item)" placeholder="Digite o item"/>
            <div class="imput-group-append">
              <button class="btn btn-info" v-on:click="addItem(item)"><span class="fa fa-plus"></span></button>
            </div>
          </div>
        </ul> <!-- fim Lista -->
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "AppItemList",
  props: ["title", "items"],
  data() {
    return {
      item:  ""
    };
  },
  methods: {
    addItem(item) {
      this.$emit("addItem", item); // evento
      this.item = "";
    },
    deleteItem(item){
      this.$emit("deleteItem", item);
    }
  }
};
</script>

<style scoped>
</style>
