<template>
  <div class="container">
    <div class="row">
      <div class="col-md-12">
        <h3>
          <hr>
          {{ msg }}
          <hr>
        </h3>
        <form action="">
          <div class="form-group">
            <label>Full Name</label>
            <input type="text" placeholder="Full Name" v-model="details.name" required class="form-control">
          </div>
          <div class="form-group">
            <label>Email Address</label>
            <input type="email" placeholder="Email Address" v-model="details.email" required class="form-control">
<!--            <div class="text-sm mt-2 text-red" v-if="v.$error">-->
<!--              <div v-if="!v.required">Email is required</div>-->
<!--              <div v-if="!v.email">Email is not a properly formatted email address</div>-->
<!--            </div>-->
          </div>
          <div class="form-group">
            <label>Date Of Birth</label>
            <input type="date" placeholder="DOB" v-model="details.date_of_birth" required class="form-control">
          </div>
          <div class="form-group">
            <label>Home Address</label>
            <input type="text" placeholder="Home address" v-model="details.home_address" required class="form-control">
          </div>
          <div class="form-group">
            <label>School Attended</label>
            <input type="text" placeholder="School Attended" v-model="details.school_attended" required
                   class="form-control">
          </div>
          <div class="form-group">
            <label>Year Finished School</label>
            <input type="number" placeholder="Year Finished School" v-model="details.year_finished_school" required
                   class="form-control">
          </div>
          <div class="form-group">
            <label>Grades Achieved</label>
            <input type="number" placeholder="Grades Achieved" v-model="details.grades_achieved" required
                   class="form-control">
          </div>
          <div class="form-group">
            <label>Courses</label>
            <select v-model="details.courses" required class="form-control">
              <option value="postgresql">PostgresSQL</option>
              <option value="spring_boot">Spring Boot</option>
              <option value="nodejs">NodeJs</option>
              <option value="laravel">Laravel</option>
            </select>
          </div>
          <div class="form-group">
            <button class="btn btn-primary float-right">SUBMIT</button>
          </div>
        </form>
      </div>
    </div>
  </div>
</template>

<script>
import {between, email, maxLength, minLength, required} from "vuelidate/lib/validators";
import Vue from "vue";
import VuelidateErrorExtractor from "vuelidate-error-extractor";

Vue.use(VuelidateErrorExtractor, {
  i18n: false,
  // Define common validation messages.
  messages: {
    required: "{attribute} is required!",
    email: "{attribute} is not a valid Email address.",
  }
});

export default {
  name: 'HelloWorld',
  props: {
    msg: String
  },
  data() {
    return {
      details: {
        name: '',
        email: '',
        date_of_birth: '',
        home_address: '',
        school_attended: '',
        year_finished_school: '',
        grades_achieved: '',
        courses: '',
      }
    }
  },
  validations: {
    name: {
      required,
      minLength: minLength(4),
      maxLength: maxLength(255),
    },
    email: {
      required,
      email,
      minLength: minLength(4),
      maxLength: maxLength(255),
    },
    date_of_birth: {
      required
    },
    home_address: {
      required,
      email,
      minLength: minLength(4),
      maxLength: maxLength(255),
    },
    school_attended: {
      required,
      email,
      minLength: minLength(4),
      maxLength: maxLength(255),
    },
    year_finished_school: {
      required,
      between: between(2000, 2020)
    },
    grades_achieved: {
      required,
      email,
      minLength: minLength(4),
      maxLength: maxLength(255),
    },
    courses: {
      required,
      email,
      minLength: minLength(4),
      maxLength: maxLength(255),
    }
  },
}
</script>
