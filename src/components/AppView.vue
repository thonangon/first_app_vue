<template>
  <div id="App">
    <h1>Subject Management (Development)</h1>
    <div class="main-input">
      <label for="subject">Subject</label>
      <input type="text" id="subject" v-model="subject" />
      <label for="description">Description</label>
      <input type="text" id="description" v-model="description" />
    </div>
    <button @click="createCard()" class="btn btn-primary">Create</button>
    <div class="search-container">
      <input id="search" type="text" placeholder="Search your favorite subject ..."
        v-model="keySearch"
      />
    </div>
    <div class="card mt-5" style="width: 50rem" v-for="(card, index) in filteredCards" :key="index">
      <div class="card-body">
        <div>
          <h5 class="card-subject">{{ card.subject }}</h5>
          <p class="card-text">{{ card.description }}</p>
        </div>
        <div>
          <button @click="deleteCard(index)" class="btn btn-danger">
            Delete
          </button>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  name: "App",
  data() {
    return {
      subject: "",
      description: "",
      cards: [
        {
          id: 1,
          subject: "HTML",
          description:
            "Some quick example description to build on the card subject and make up the bulk of the card's content.",
          completed: false,
        },
        {
          id: 2,
          subject: "CSS",
          description:
            "Some quick example description to build on the card subject and make up the bulk of the card's content.",
          completed: false,
        },
        {
          id: 3,
          subject: "JavaScript",
          description:
            "Some quick example description to build on the card subject and make up the bulk of the card's content.",
          completed: false,
        },
      ],
      keySearch: "",
    };
  },
  methods: {
    createCard() {
      this.cards.push({
        id: this.cards.length + 1,
        subject: this.subject,
        description: this.description,
        completed: false,
      });
      this.subject = "";
      this.description = "";
    },
    deleteCard(index) {
      this.cards.splice(index, 1);
    },
  },
  computed: {
    filteredCards() {
      if (this.keySearch === "") {
        return this.cards;
      } else {
        return this.cards.filter((card) =>
          card.subject.toLowerCase().includes(this.keySearch.toLowerCase())
        );

      }
    },
  },
};
</script>

<style>
.card {
  width: 50rem;
  margin: 0 auto;
  margin-top: 10px;
}
.card-body {
  display: flex;
  justify-content: space-between;
}
.main-input {
  margin: 30px;
}
.search-container {
  width: 50%;
  margin: auto;
  height: 2rem;
  display: flex;
  margin-top: 20px;
}
.search-container input {
  width: 80%;
  padding: 10px;
  box-sizing: border-box;
}
.search-container button {
  padding: 4px;
  border: none;
  width: 9%;
  background: #198cc2;
  color: #fff;
  font-size: 15px;
  cursor: pointer;
}
</style>
