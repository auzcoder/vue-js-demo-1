<script>
export default {
  data() {
    return {
      name: '',
      viewers: '',
    }
  },
  methods: {
    addMovie() {
      if (!this.name || !this.viewers) return
      const newMovie = {
        id: Date.now(),
        name: this.name,
        viewers: this.viewers,
        favourite: false,
        like: false,
      }
      this.$emit('createMovie', newMovie)
      this.name = ''
      this.viewers = ''
    },
  },
}



</script>

<template>
  <div class="movie-add-form" @submit.prevent>
    <h3>Kino qo'shish</h3>
    <form class="add-form d-flex needs-validation" novalidate>
      <input type="text"
         class="form-control"
         placeholder="Kino nomi?"
         :value="name"
         @input="name = $event.target.value"
         required
      />
      <input type="number"
          class="form-control new-movie-label"
          placeholder="Necha marta ko'rilgan?"
          :value="viewers"
          @input="viewers = $event.target.value"
      />
      <button class="btn btn-outline-success" type="submit" @click="addMovie">Qo'shish</button>
    </form>
  </div>
</template>

<style scoped>
.movie-add-form {
  margin-top: 2rem;
  padding: 1.5rem;
  background-color: #fcfaf5;
  border-radius: 4px;
  box-shadow: 15px 15px 15px rgba(0, 0, 0, 0.15);
}
</style>