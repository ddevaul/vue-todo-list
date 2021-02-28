<template>
  <div class="container">
    <input v-model="title" placeholder="edit me">
    <button @click="create">Create</button>
  </div>
</template>

<script>
export default {
  name: 'todoitem',
  data() {
    return {
      title: '',
    };
  },
  methods: {
    create() {
      this.$emit('createItem', this.title);
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
