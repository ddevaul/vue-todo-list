<template>
  <h1>ToDo List</h1>
  <CreateItem @createItem='create'></CreateItem>
  <Todoitem
    v-for='item in items'
    :key='item.id'
    :item='item'
    @changeEvent="updateTitle(item.id, $event)"
    @completeEvent="toggleCompleted(item.id)"
    @deleteEvent="deleteItem(item.id)"
    >
  </Todoitem>
</template>

<script>
import Todoitem from './components/Todoitem.vue';
import CreateItem from './components/CreateItem.vue';

export default {
  name: 'App',
  components: {
    Todoitem,
    CreateItem,
  },
  data() {
    return {
      newTitle: '',
      items: [{ title: 'asdf', completed: false, id: 1 }, { title: 'asdf2', completed: false, id: 2 }],
    };
  },
  methods: {
    create(newTitle) {
      const { length } = this.items;
      const { id } = this.items[length - 1];
      this.items.push({ title: newTitle, completed: false, id: id + 1 });
    },
    deleteItem(itemid) {
      this.items = this.items.filter((i) => i.id !== itemid);
    },
    updateTitle(itemid, newTitle) {
      const itemArray = this.items.filter((i) => i.id === itemid);
      const item = itemArray[0];
      item.title = newTitle;
    },
    toggleCompleted(itemid) {
      const itemArray = this.items.filter((i) => i.id === itemid);
      const item = itemArray[0];
      item.completed = !item.completed;
    },
  },
};
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
