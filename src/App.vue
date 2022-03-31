<script>
export default{
  data() {
    return {
      type: "dog",
      pets: [
        {id: 1, type: "dog", name: "Hunter", desc: "Hunter is a small puppy, he likes to play and he's 6 months old", picture: 'dog1.jpg'},
        {id: 2, type: "dog", name: "Bruno", desc: "Bruno is 2 years old and loves to run in the park", picture: 'dog2.jpg'},
        {id: 3, type: "dog", name: "Paco", desc: "Paco is 4 years old and likes to sleep and play with other dogs", picture: 'dog3.jpg'},
        {id: 4, type: "cat", name: "Milo", desc: "Milo loves treats and is 1 year old", picture: 'cat1.jpg'},
        {id: 5, type: "cat", name: "Loki", desc: "Loki is 2 years old and hates everyone", picture: 'cat2.jpg'},
        {id: 6, type: "cat", name: "Felix", desc: "Felix is a 3 year old cat and is very happy", picture: 'cat3.jpeg'}
      ],
      myPets: "...",
      otherPets: [
        {id: 1, animal: "Tortoise"},
        {id: 2, animal: "Hamster"},
        {id: 3, animal: "Hedgehog"}
      ],
      picked: "tort",
    }
  },
  methods: {
    dogMode() { this.type = "dog" },
    catMode() { this.type = "cat" },
  },
}
</script>


<template>
  <div>
    <nav class="navbar navbar-expand-lg navbar-dark bg-primary">
      <div class="container-fluid">
        <h1 class="navbar-brand">Awesome Pet Application</h1>
        <button class="navbar-toggler" type="button" data-bs-toggle="collapse" data-bs-target="#navbarNavAltMarkup" aria-controls="navbarNavAltMarkup" aria-expanded="false" aria-label="Toggle navigation">
          <span class="navbar-toggler-icon"></span>
        </button>
        <div class="collapse navbar-collapse" id="navbarNavAltMarkup">
          <div class="navbar-nav">
            <a @click.prevent="dogMode" class="nav-link" aria-current="page">Dogs 🐶</a>
            <a @click.prevent="catMode" class="nav-link">Cats 🐱</a>
            <a @click.prevent="type='other'" class="nav-link">Other pets</a>
          </div>
        </div>
      </div>
    </nav>

    <!-- v-if -->
    <h1 v-if="type === 'dog'">Dog Page 🐶</h1>
    <h1 v-else-if="type === 'cat'">Cat Page 🐱</h1>
    <h1 v-else>Pet Carousel! 🐢🐹🦔</h1>

    <!-- Cards de animales -->
    <div>
      <!-- CARDS DE PERROS Y GATOS -->
      <div v-if="type === 'dog' || type === 'cat'" class="card-container">
        <!-- For -->
        <div v-for="pet in pets.filter(p => p.type === type)" :key="pet.id" class="card" style="width: 18rem;">
          <div class="card-body">
            <img v-if="pet.id === 1" src="./assets/dog1.jpg">
            <img v-if="pet.id === 2" src="./assets/dog2.jpg">
            <img v-if="pet.id === 3" src="./assets/dog3.jpg">
            <img v-if="pet.id === 4" src="./assets/cat1.jpg">
            <img v-if="pet.id === 5" src="./assets/cat2.jpg">
            <img v-if="pet.id === 6" src="./assets/cat3.jpeg">
            <h2 class="card-title">{{pet.name}}</h2>
            <h5>{{pet.desc}}</h5>
          </div>
        </div>
      </div>

      <!-- CARDS DE OTHER PETS (CAROUSEL) -->
      <div v-else class="alert alert-secondary other-pets">
        <img v-if="picked === 'tort'" src="./assets/pet1.jpg" class="center">
        <img v-if="picked === 'hamst'" src="./assets/pet2.jpg" class="center">
        <img v-if="picked === 'hedg'" src="./assets/pet3.jpg" class="center">

        <h2 v-if="picked === 'tort'">Tortoise</h2>
        <h2 v-if="picked === 'hamst'">Hamster</h2>
        <h2 v-if="picked === 'hedg'">Hedgehog</h2>

        <div class="center">
          <input type="radio" id="tortoise" value="tort" v-model="picked" />
          <label for="tortoise">Tortoise</label>

          <input type="radio" id="hamster" value="hamst" v-model="picked" />
          <label for="hamster">Hamster</label>

          <input type="radio" id="hedgehog" value="hedg" v-model="picked" />
          <label for="hedgehog">Hedgehog</label>
        </div>
      </div>

    </div>

    <!-- 2 way binding -->
    <div id="binding" class="alert alert-info">
      <h2>Hi, random viewer! I have a dog 🐶 and a tortoise 🐢 as pets. Do you have any?</h2>
      <h3>-- Hi, Memo! I have {{myPets}}</h3>
      <input v-model="myPets"/>
    </div>

  </div>
</template>

<style>
  * {
    box-sizing: border-box;
    margin: 0;
    padding: 0;
  }
  
  html,
  body {
    font-family: Arial, Helvetica, sans-serif;
  }
  
  h1,
  h2,
  h3 {
    text-align: center;
    margin-bottom: 1rem;
    font-weight: normal;
  }
  
  button {
    cursor: pointer;
    display: inline-block;
    background: #333;
    color: white;
    font-size: 18px;
    border: 0;
    padding: 1rem 1.5rem;
    text-align: center;
  }
  
  button:focus {
    outline: none;
  }

  .card-container {
    display: flex;
    justify-content: center;
    flex-direction: row;
    flex-wrap: wrap;
  }

  .card {
    margin: 5px;
  }

  img {
    width: 15rem;
    height: 15rem;
  }

  #binding {
    border-color: black;
    border-style: solid;
    text-align: center;
    margin: auto;
    margin-top: 10%;
    width: 50%;
  }

  .center {
    margin: auto;
    width: 30rem;
    text-align: center;
  }

  .other-pets {
    margin: auto;
    width: 50%;
    display: flex;
    flex-direction: column;
    align-content: center;
  }
</style>
