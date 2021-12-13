<template>
  <div id="app">
    <div class="row container">
      <div class="col-md-3">
        <h3 class="heading">VIDEO GAMES</h3>
        <div class="formSearch">
          <p>Filter Results</p>
          <form v-on:submit="clear">
            <div class="form-group">
              <label for="name">Name (contains)</label>
              <input
                type="text"
                style="background-color: #182c47; border: none;color:#ffffff;"
                class="form-control"
                id="name"
                v-model="name"
                v-on:keydown.enter.prevent="searchByName"
              />
            </div>
            <div class="form-group">
              <label for="score">Minimum Score</label>
              <input
                type="number"
                style="background-color: #182c47; border: none;color:#ffffff;"
                class="form-control"
                v-model="score"
                v-on:keydown.enter.prevent="searchByScore"
                id="score"
              />
            </div>
            

            <button type="submit" class="btn">Clear</button>
          </form>
        </div>
      </div>
      <div class="col-md-9">
        <h3 class="heading">CONTACT</h3>
        <div v-if="!resultCount">
          <ul v-for="game in games" :key="game.id">
            <div class="card mb-3 w-max" style="background-color: #0e1a2b">
              <div class="row no-gutters mt-0 pt-0">
                <div class="col-md-2 bg-black"></div>
                <div class="col-md-10">
                  <div class="card-body">
                    <h5 class="card-title" style="color: #ffffff">
                      {{ game.name }}
                    </h5>
                    <p class="card-text">{{ game.summary }}</p>
                    <span class="rate rounded-circle px-2">{{ (game.rating / 10).toFixed(1)  }}</span>
                  </div>
                </div>
              </div>
            </div>
          </ul>
        </div>
        <div v-if="resultCount">
          <ul v-for="res in result" :key="res.id">
            <div class="card mb-3 w-max" style="background-color: #0e1a2b">
              <div class="row no-gutters mt-0 pt-0">
                <div class="col-md-2 bg-black"></div>
                <div class="col-md-10">
                  <div class="card-body">
                    <h5 class="card-title" style="color: #ffffff">
                      {{ res.name }}
                    </h5>
                    <p class="card-text">{{ res.summary }}</p>
                    <span class="rate rounded-circle px-2">{{ (res.rating / 10).toFixed(1)  }}</span>
                  </div>
                </div>
              </div>
            </div>
          </ul>
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
      games: [],
      name: "",
      score: 0,
      result: [],
      resultCount: false,
    };
  },
  methods: {
    async getGames() {
      try {
        const response = await fetch(
          "https://public.connectnow.org.uk/applicant-test/"
        );
        const data = await response.json();
        this.games = data;
      } catch (error) {
        console.error(error);
      }
    },
    searchByName() {
      //e.preventDefault(); // it prevent from page reload
      this.result = [];
      this.games.forEach((game, index) => {
        if (game.name == this.name) {
          console.log(index);
          this.result.push(game);
          this.resultCount = true;
        }
      });
      this.result.sort(this.selected);
    },
    searchByScore() {
      this.result = [];
      this.games.forEach((game, index) => {
        if (game.rating / 10 >= this.score) {
          console.log(index);
          this.result.push(game);
          this.resultCount = true;
        }
      });
    },
    
    clear(e) {
      e.preventDefault();
      this.name = "";
      this.score = 0;
      this.resultCount = false;
    },
  },
  mounted() {
    this.getGames();
  },
};
</script>

<style>
.row {
  padding-top: 50px;
}
.card {
  background-color: #0e1a2b;
}
.btn {
  background-color: #5692e8 !important;
  margin-top: 40px !important;
  color: #ffffff !important;
  
  font-family: 'Montserrat', sans-serif;
}
.rate {
  background-color: #5692e8;
  padding: 6px;
  position: absolute;
  top: 8px;
  right: 5px;
  font-size: 24px;
  color: #ffffff;
}
.form-group {
  margin-bottom: 20px;
  margin-left: 5px;
  margin-right: 5px;
}
.form-control {
  background-color: #182c47;
  border: none;
  font-family: 'Montserrat', sans-serif;
}
.formSearch {
  background-color: #0e1a2b;
  padding: 10px;
  padding-bottom: 100px;
}
.heading {
  color: #ffffff;
  margin-bottom: 20px;
}
</style>
