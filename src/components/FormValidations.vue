<template>
  <form @submit="checkForm" novalidate="true">
    <div class=" form-group">
        <p v-if="errors.length">You need to correct these following errors</p>
        <ul>
            <li class="text-danger " v-for="(error, index) in errors" :key="index" >{{ error }}</li>
        </ul>
    </div>
    <div class="form-group col-4">
      <label for="name">Name</label>
      <input
        class="form-control"
        id="name"
        v-model="name"
        type="text"
        name="name"
      />
    </div>
    <div class="form-group col-4">
      <label for="name">Email</label>
      <input
        class="form-control"
        id="email"
        v-model="email"
        type="email"
        name="email"
      />
    </div>
    <div class="form-group col-4">
      <label for="age">Age</label>
      <input
        class="form-control"
        id="age"
        v-model="age"
        type="number"
        name="age"
        min="0"
      />
    </div>
    <div class="form-group col-4">
      <label for="tickets">Tickets </label>
      <input
        class="form-control"
        id="tickets"
        v-model="tickets"
        type="number"
        name="tickets"
        min="0"
      />
    </div>
    <div class="form-group col-4">
      <label for="movie">Select Movie</label>
      <select id="movie" v-model="movie" name="movie" class="form-control">
        <option>Star Wars</option>
        <option>Vanilla Sky</option>
        <option>Atomic Blonde</option>
      </select>
    </div>
    <div class="form-group col-4">
      <input class="btn btn-primary" type="submit" value="Submit" />
    </div>
  </form>
</template>

<script>
export default {
  name: "FormValidations",
  data() {
    return {
      errors: [],
      name: null,
      email: null,
      age: null,
      movie: null,
      tickets: null,
    };
  },
  methods: {
    checkForm: function(e) {
      e.preventDefault();

      this.errors = [];
      if (this.errors.length) return;

      //Add validations for required attributes
      if (!this.name) {
        this.errors.push("Name is Required");
      }

      if (!this.email) {
        this.errors.push("Email is Required");
      } else if (!this.validEmail(this.email)) {
        this.errors.push("Ivalid email");
      }

      if (!this.age) {
        this.errors.push("Age is Required");
      }

      if (!this.movie) {
        this.errors.push("Movie is Required");
      }

      if (!this.tickets) {
        this.errors.push("Tickets is Required");
      }
      //if there is no error then return the true
      if (!this.errors.length) return true;
    },

    validEmail: function(email) {
      var re = /^(([^<>()\[\]\\.,;:\s@"]+(\.[^<>()\[\]\\.,;:\s@"]+)*)|(".+"))@((\[[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\.[0-9]{1,3}\])|(([a-zA-Z\-0-9]+\.)+[a-zA-Z]{2,}))$/;
      return re.test(email);
    },
  },
};
</script>
