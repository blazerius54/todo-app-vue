<template>
  <div class='ui basic content center aligned segment'>
    <button class='ui basic button icon' v-on:click="toggleForm" v-show="!isCreating">
      <i class='plus icon'></i>
    </button>
    <div class='ui centered card' v-show="isCreating">
      <div class='content'>
        <div class='ui form'>
          <div class='field'>
            <label>Title</label>
            <input v-model="titleText" type='text' ref='title' defaultValue="">
          </div>
          <div class='field'>
            <label>Project</label>
            <input v-model='project' type='text' ref='project' defaultValue="">
          </div>
          <div class='ui two button attached buttons'>
            <button class='ui basic blue button' v-on:click="sendForm">
              Create
            </button>
            <button class='ui basic red button' v-on:click="toggleForm">
              Cancel
            </button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>
<script>

export default {
    data() {
        return {
            isCreating: false,
            titleText: '',
            project: ''

        }
    },
    methods: {
        toggleForm() {
            this.isCreating = !this.isCreating
        },
        sendForm() {
          const title = this.titleText;
          const project = this.project;
          this.$emit('create-todo', {
            title,
            project,
            done: false
          });
          this.toggleForm();
          this.titleText = '';
          this.Project = '';
        }
    }
}

</script>