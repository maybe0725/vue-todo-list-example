<template>
  <div>
    <v-card
      class="pa-3 mb-3"
      :class="{'done': list.status === 'done'}"
      v-for="(list, index) in todoList"
      :key="index"
    >
      <p>{{list.memo}}</p>
      <!--
      <v-btn
        v-if="list.status === 'created'"
        fab
        small
        color="green"
        @click="$emit('statusControll', index, 'done')"
      >
        <i class="fas fa-check"></i>
      </v-btn>
      <v-btn
        v-if="list.status === 'done'"
        fab
        small
        color="blue"
        @click="$emit('statusControll', index, 'created')"
      >
        <i class="fas fa-redo-alt"></i>
      </v-btn>
      <v-btn fab small color="red" @click="$emit('listDelete', index)">
        <i class="fas fa-trash-alt"></i>
      </v-btn>
      <v-btn
        v-if="list.status === 'created'"
        fab
        small
        color="yellow"
        @click="listEdit(list.memo, index)"
      >
        <i class="fas fa-edit"></i>
      </v-btn>
      -->
      <v-icon
        v-if="list.status === 'created'"
        fab
        small
        class="pa-3"
        color="green"
        @click="$emit('statusControll', index, 'done')"
      >fas fa-check</v-icon>
      <v-icon
        v-if="list.status === 'done'"
        fab
        small
        class="pa-3"
        color="blue"
        @click="$emit('statusControll', index, 'created')"
      >fas fa-redo-alt</v-icon>
      <v-icon
        fab
        small
        class="pa-3"
        color="red"
        @click="$emit('listDelete', index)"
      >fas fa-trash-alt</v-icon>
      <v-icon
        v-if="list.status === 'created'"
        fab
        small
        class="pa-3"
        color="yellow"
        @click="listEdit(list.memo, index)"
      >fas fa-edit</v-icon>
    </v-card>
  </div>
</template>

<script>
import { eventBus } from "../main.js";
export default {
  props: ["todoList"],
  methods: {
    listEdit(memo, index) {
      eventBus.listEdit(memo, index);
    }
  }
};
</script>

<style scoped>
.done {
  background-color: rgba(0, 0, 0, 0.1);
}
.done p {
  text-decoration: line-through;
  color: rgba(0, 0, 0, 0.5);
}
</style>