
<template>
  <h1>Hello world {{ name }}</h1>

  <p v-if="professor">User is a professor</p>
  <p v-else>User is not a professor</p>

  <p v-if="age >= 18">User is 18+</p>
  <p v-else>User is not 18</p>

  <ol>
    <li v-on:click="deleteClass(singleClass)" v-for="singleClass in classes" :key="singleClass">{{ singleClass }}</li>
  </ol>

  <form @submit.prevent>
    <input v-model="name" type="text" placeholder="Unesite vase ime" />
  </form>

  <form @submit.prevent>
    <input ref="classInputName" v-on:keyup="checkClassNameValidity" type="text" placeholder="Unesite ime kursa" />
    <input :disabled="disabledClassButton" v-on:click="addClass" type="button" value="Dodajte kurs" />
  </form>

  <button v-on:click="changeUserType">Promeni tipa korisnika</button>
</template>

<script>

export default {
  name: "App",
  data() {
    return {
      name: "Toma",
      professor: false,
      age: 11,
      classes: ['Javascript', 'VueJS', 'ReactJS', 'NodeJS'],
      disabledClassButton: true,
    }
  },
  methods: {
    changeUserType() {
      this.professor = !this.professor;
    },

    deleteClass(name) {
      const index = this.classes.indexOf(name); // 0, 1, 2, 3
      this.classes.splice(index, 1);
    },

    addClass() {
      const className = this.$refs.classInputName.value;
      this.classes.push(className);
    },

    checkClassNameValidity() {

      const className = this.$refs.classInputName.value;
      const courses = this.classes.map(val => val.toLowerCase());
      const courseName = className.toLowerCase();

      if(className.trim() === "") {
        this.disabledClassButton = true;
      } else this.disabledClassButton = courses.includes(courseName); // courses.includes(courseName); -> True / False
    }
  }
}
</script>