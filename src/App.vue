<template>
  <div id="app">
    <header>
      <img alt="Vue logo" class="logo" v-bind:src="url" width="125" height="125" />

      <div class="wrapper">
        <h1>Let's go!</h1>
      </div>
    </header>

    <main>
      <label>Objetos: </label>
      <input type="number" v-model="items">
      <p v-if="items > 1">Tienes {{items}} objetos</p>
      <p v-else-if="items <= 0">No tienes objetos</p>
      <p v-else>Tienes {{items}} objeto</p>
      <input type="radio" id="one" value="uno" v-model="picked" />
      <label for="one">Uno</label>
      <br>
      <input type="radio" id="two" value="dos" v-model="picked" />
      <label for="two">Dos</label>
      <p>Quieres {{picked}}</p>
      <form>
        <div>
          <label for="name">Nombre: </label>
          <input type="text" id="name" name="name" v-model="fname">
        </div>
        <div>
          <label for="email">Email: </label>
          <input type="email" id="email" name="email" v-model="email">
        </div>
        <div>
          <label for="phone">Teléfono: </label>
          <input type="tel" id="phone" name="phone" v-model="phone">
        </div>
        <div>
          <label for="message">Consulta: </label>
          <textarea type="textarea" name="message" id="message" v-model="message"></textarea>
        </div>
        <button v-on:click="send">Enviar</button>
      </form>
      <hr>
      <div v-html="formHtml"></div>
      <span v-if="!tasks">Cargando...</span>
      <div v-for="task in tasks" :key="task.name">
        <h3>{{task.name}}</h3>
        <p>{{task.when}}</p>
      </div>
    </main>
    <counter/>
    <posts v-bind:posts="posts"/>
  </div>
</template>

<script>
import Counter from './components/Counter.vue';
import Posts from './components/Posts.vue';
export default{
  name: 'App',
  components: {Counter, Posts},
  data(){

    return{
      items: 0,
      picked: '',
      fname: '',
      email: '',
      phone: '',
      message: '',
      tasks: [
        {name: 'Aprender Vue', when: 'Todos los días'},
        {name: 'Dar estilos proyecto', when: 'Martes'},
        {name: 'Lavarme los dientes', when: 'Después de cada comida'}
      ],
      url: 'https://upload.wikimedia.org/wikipedia/commons/f/f1/Vue.png',
      formHtml: '',
      posts: [
        {
          id: 1,
          title: "Lorem"
        },
        {
          id: 2,
          title: "Ipsum"
        },
        {
          id: 3,
          title: "Veracitum"
        },
        {
          id: 4,
          title: "Programmanum"
        }
      ]
    }
  },
  methods:{
    send(e){
      e.preventDefault();
      this.formHtml = `
        <p>Nombre: ${this.fname}</p>
        <p>Email: ${this.email}</p>
        <p>Teléfono: ${this.phone}</p>
        <p>Consulta: ${this.message}</p>
      `
    }
  }
}
</script>

<style scoped>
header {
  line-height: 1.5;
}

.logo {
  display: block;
  margin: 0 auto 2rem;
}

@media (min-width: 1024px) {
  header {
    display: flex;
    place-items: center;
    padding-right: calc(var(--section-gap) / 2);
  }

  .logo {
    margin: 0 2rem 0 0;
  }

  header .wrapper {
    display: flex;
    place-items: flex-start;
    flex-wrap: wrap;
  }
}
</style>
