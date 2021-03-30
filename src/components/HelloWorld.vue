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
<!--            <p class="text-danger" v-if="!$v.name.required">The name field is required!</p>-->
          </div>
          <div class="form-group">
            <label>Email Address</label>
            <input type="email" placeholder="Email Address" v-model="details.email" required class="form-control">
<!--            <p class="text-danger" v-if="!$v.email.required">The email field is required!</p>-->
<!--            <p class="text-danger" v-if="!$v.email.email">The input must be a proper email!</p>-->
          </div>
          <div class="form-group">
            <label>Date Of Birth</label>
            <input type="date" placeholder="DOB" v-model="details.date_of_birth" required class="form-control">
<!--            <p class="text-danger" v-if="!$v.date_of_birth.required">The dob field is required!</p>-->
          </div>
          <div class="form-group">
            <label>Home Address</label>
            <input type="text" placeholder="Home address" v-model="details.home_address" required class="form-control">
<!--            <p class="text-danger" v-if="!$v.home_address.required">The home address field is required!</p>-->
          </div>
          <div class="form-group">
            <label>School Attended</label>
            <input type="text" placeholder="School Attended" v-model="details.school_attended" required
                   class="form-control">
<!--            <p class="text-danger" v-if="!$v.school_attended.required">The school attended field is required!</p>-->
          </div>
          <div class="form-group">
            <label>Year Finished School</label>
            <input type="number" placeholder="Year Finished School" v-model="details.year_finished_school" required
                   class="form-control">
<!--            <p class="text-danger" v-if="!$v.year_finished_school.required">The year of finish field is required!</p>-->
          </div>
          <div class="form-group">
            <label>Grades Achieved</label>
            <input type="text" placeholder="Grades Achieved" v-model="details.grades_achieved" required
                   class="form-control">
<!--            <p class="text-danger" v-if="!$v.grades_achieved.required">The grades field is required!</p>-->
          </div>
          <div class="form-group">
            <label>Courses</label>
            <select v-model="details.courses" required class="form-control">
              <option value="courses" disabled selected>Select Courses</option>
              <option value="postgresql">PostgresSQL</option>
              <option value="spring_boot">Spring Boot</option>
              <option value="nodejs">NodeJs</option>
              <option value="laravel">Laravel</option>
            </select>
<!--            <p class="text-danger" v-if="!$v.courses.required">The courses field is required!</p>-->
          </div>
          <div class="form-group">
            <button @click="submitForm()" class="btn btn-primary float-right">SUBMIT</button>
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
  methods: {
    submitForm() {
      this.$swal({
        title: 'Are you sure?',
        text: 'You can\'t revert your action',
        type: 'warning',
        showCancelButton: true,
        confirmButtonText: 'Yes Update it!',
        cancelButtonText: 'No, Keep it!',
        showCloseButton: true,
        showLoaderOnConfirm: true
      }).then((result) => {
        if (result.value) {
          this.$swal('Details Submitted Successfully', 'Submit successfully', 'success');
        } else {
          this.$swal('Cancelled', 'Your data is still intact', 'error')
        }
      });
    }
  }
}
</script>
