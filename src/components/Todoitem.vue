<template>
  <div class="container">
    <input @input="createChangeEvent" v-model="title">
    <input @click="createCompleteEvent" v-model="completed" type="checkbox">
    <button @click="createDeleteEvent">delete</button>
    <div v-if="completed">COMPLETED</div>
  </div>
</template>
<script>
export default {
  name: 'todoitem',
  props: {
    item: { required: true, type: Object },
  },
  data() {
    return {
      title: this.item.title,
      completed: this.item.completed,
    };
  },
  methods: {
    createChangeEvent() {
      this.$emit('changeEvent', this.title);
    },
    createCompleteEvent() {
      this.$emit('completeEvent');
    },
    createDeleteEvent() {
      this.$emit('deleteEvent');
    },
  },
};
</script>
<style scoped>
.container {
  width: 600px;
  display: flex;
  flex-direction: column;
  align-items: center;
  border: 2px solid rgb(142, 193, 255);
  margin: 10px auto;
}
.container input{
  width: 500px;
  height: 50px;
  font-size: 40px;
  text-align: center;
  margin: 10px;
}
.container button{
  height: 40px;
  font-size: 30px;
  margin: 10px;
}
</style>
