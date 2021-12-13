<template>
  <div class="body overflow-auto">
    <games />
    <!-- <contact/> -->
  </div>
</template>

<script>
import games from "@/components/games";
//import contact from "@/components/contact";
export default {
  components: {
    games,
  //contact
  },
};
</script>

<style>
@import url('https://fonts.googleapis.com/css2?family=Montserrat:wght@500;600&display=swap');
@import url('https://fonts.googleapis.com/css2?family=Mulish:wght@500&display=swap');

.body {
  position: fixed;
  top: 0;
  right: 0;
  left: 0;
  bottom: 0;
  background-image: repeating-linear-gradient(#081221, #03080f);
  color: #c1d1e8;
  font-family: 'Mulish', sans-serif;
}
.heading {
  color: #ffffff;
  margin-bottom: 20px;
  font-family: 'Montserrat', sans-serif;
}
.row {
  padding-top: 50px;
}
.formSearch {
  background-color: #0e1a2b;
  padding: 10px;
  padding-bottom: 100px;
}



</style>
