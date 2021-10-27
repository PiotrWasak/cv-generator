<template>
  <div class="main container">
    <form>
      <div class="row">
        <div class="col-md-6">
          <i class="fas fa-id-card"></i>
        </div>
        <div class="col-md-6"><p class="h4">Personal data</p></div>
      </div>
      <br />
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label for="firstName">First name*</label>
            <input
              v-model="v$.firstName.$model"
              :class="status(v$.firstName)"
              type="text"
              class="form-control"
              id="firstName"
            />
            <div class="error-message" v-if="!v$.firstName.required">
              Field is required
            </div>
          </div>
        </div>
        <div class="col-md-6">
          <div class="form-group">
            <label for="lastName">Last name*</label>
            <input
              v-model="v$.lastName.$model"
              :class="status(v$.lastName)"
              type="text"
              class="form-control"
              id="lastName"
            />
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-7">
          <div class="form-group">
            <label for="email">E-mail*</label>
            <input
              v-model="v$.email.$model"
              :class="status(v$.email)"
              type="email"
              class="form-control"
              id="email"
            />
          </div>
        </div>
        <div class="col-md-5">
          <div class="form-group">
            <label for="phoneNumber">Phone number</label>
            <input
              v-model="v$.phoneNumber.$model"
              :class="status(v$.phoneNumber)"
              type="text"
              class="form-control"
              id="phoneNumber"
            />
          </div>
        </div>
      </div>
      <div class="row">
        <div class="form-group">
          <label for="address">Address</label>
          <input
            v-model="address"
            type="text"
            class="form-control"
            id="address"
          />
        </div>
      </div>
      <div class="row">
        <div class="col-md-3">
          <div class="form-group">
            <label for="postal">Postal code</label>
            <input
              v-model="postalCode"
              type="text"
              class="form-control"
              id="postal"
            />
          </div>
        </div>
        <div class="col-md-9">
          <div class="form-group">
            <label for="city">City</label>
            <input v-model="city" type="text" class="form-control" id="city" />
          </div>
        </div>
      </div>
      <div v-if="isAddInfoVisible" id="additionalInfo">
        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label for="dob">Date of birth</label>
              <input v-model="dob" type="date" class="form-control" id="dob" />
            </div>
          </div>
          <div class="col-md-6">
            <div class="form-group">
              <label for="sex">Sex</label>
              <select v-model="sex" class="form-control" name="sex" id="sex">
                <option>Male</option>
                <option>Female</option>
              </select>
            </div>
          </div>
        </div>

        <div class="row">
          <div class="col-md-6">
            <div class="form-group">
              <label for="webPage">Web page</label>
              <input
                v-model="webPage"
                type="text"
                class="form-control"
                id="webPage"
              />
            </div>
          </div>
          <div class="col-md-6">
            <div class="form-group">
              <label for="nationality">Nationality</label>
              <input
                v-model="nationality"
                type="text"
                class="form-control"
                id="nationality"
              />
            </div>
          </div>
        </div>
      </div>
      <!-- Additional info -->
      <br />
      <div class="row">
        <button
          @click="toggleAdditionalInfo()"
          type="button"
          id="additionalInfo"
          class="btn btn-secondary"
        >
          {{ addBtnText }}
        </button>
      </div>
      <br />
      <hr />
      <br />

      <div class="row">
        <div class="col-md-6">
          <i class="fas fa-briefcase"></i>
        </div>
        <div class="col-md-6">
          <p class="h4">Work experience / education</p>
        </div>
      </div>
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label for="job">Job</label>
            <input v-model="job" type="text" class="form-control" id="job" />
          </div>
        </div>
        <div class="col-md-6">
          <div class="form-group">
            <label for="employer">Employer</label>
            <input
              v-model="employer"
              type="text"
              class="form-control"
              id="employer"
            />
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-md-6">
          <div class="form-group">
            <label for="school">School</label>
            <input
              v-model="school"
              type="text"
              class="form-control"
              id="school"
            />
          </div>
        </div>
        <div class="col-md-6">
          <div class="form-group">
            <label for="subject">Subject</label>
            <input
              v-model="subject"
              type="text"
              class="form-control"
              id="subject"
            />
          </div>
        </div>
      </div>
      <br />
      <div class="row">
        <button
          type="button"
          data-bs-toggle="modal"
          data-bs-target="#CVModal"
          id="submitBtn"
          class="btn btn-primary"
        >
          Generate CV <i class="fas fa-chevron-right"></i>
        </button>
      </div>
    </form>

    <!-- Modal -->
    <div
      class="modal fade"
      id="CVModal"
      data-bs-backdrop="static"
      tabindex="-1"
      aria-labelledby="exampleModalLabel"
      aria-hidden="true"
    >
      <div class="modal-dialog modal-xl modal-dialog-scrollable">
        <div class="modal-content">
          <div class="modal-header">
            <h5 class="modal-title" id="exampleModalLabel">
              CV: {{ firstName }} {{ lastName }}
            </h5>
            <button
              type="button"
              class="btn-close"
              data-bs-dismiss="modal"
              aria-label="Close"
            ></button>
          </div>
          <div class="modal-body">
            <div class="cv-container">
              <header class="cv-header">
                <p>Resume</p>
                <p></p>
              </header>
              <div class="row">
                <p class="lead">{{ firstName }} {{ lastName }}</p>
              </div>
              <div class="row">
                <div class="col-md-6">
                  <div class="personal-data">
                    <h4 class="h4">
                      <i class="fas fa-id-card"></i> Personal data
                    </h4>

                    E-mail: {{ email }}
                    <br />
                    Phone-number: {{ phoneNumber }}
                    <br />
                    Address: {{ address }} {{ postalCode }}, {{ city }}
                    <br />
                    Date of birth: {{ dob }}
                    <br />
                    Sex: {{ sex }}
                    <br />
                    Website: {{ webPage }}
                    <br />
                    Nationality: {{ nationality }}
                  </div>
                </div>
                <div class="col-md-6">
                  <h4 class="h4">
                    <i class="fas fa-user-graduate"></i> Education
                  </h4>
                  School: {{ school }}
                  <br />
                  Subject: {{ subject }}
                  <br />
                  <br />
                  <h4 class="h4">
                    <i class="fas fa-briefcase"></i> Work experience
                  </h4>
                  Job: {{ job }}
                  <br />
                  Employer: {{ employer }}
                </div>
              </div>
            </div>
          </div>
          <div class="modal-footer">
            <button type="button" class="btn btn-primary">Save file</button>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import { useVuelidate } from "@vuelidate/core";
import { required, minLength, email, numeric } from "@vuelidate/validators";

export default {
  name: "CVForm",
  props: {},
  data() {
    return {
      v$: useVuelidate(),
      isAddInfoVisible: false,
      firstName: "",
      lastName: "",
      email: "",
      phoneNumber: "",
      address: "",
      postalCode: "",
      city: "",
      dob: new Date(),
      sex: "",
      webPage: "",
      nationality: "",
      job: "",
      employer: "",
      school: "",
      subject: "",
    };
  },
  validations() {
    return {
      firstName: {
        required,
        minLength: minLength(2),
      },
      lastName: {
        required,
        minLength: minLength(2),
      },
      email: {
        required,
        email,
      },
      phoneNumber: {
        required,
        numeric,
      },
    };
  },
  computed: {
    addBtnText() {
      let text = "";
      this.isAddInfoVisible === true
        ? (text = "➖ Hide additional info")
        : (text = "➕ Show additional info");
      return text;
    },
  },
  methods: {
    toggleAdditionalInfo() {
      this.isAddInfoVisible = !this.isAddInfoVisible;
    },
    status(validation) {
      return {
        error: validation.$error,
        dirty: validation.$dirty,
      };
    },
  },
  updated() {
    console.log(this.v$.firstName);
  },
};
</script>

<style scoped>
.personal-data {
  border-right: 1px solid grey;
}
.h4 {
  color: rgb(84, 36, 185);
}

.cv-container .h4 {
  color: #4a7c59;
}

.main {
  margin-top: 4em;
  margin-bottom: 4em;
  width: 40%;
  border-radius: 10px;
  background: #ffffff;
  padding: 3em;
  box-shadow: 0 15px 35px rgb(50 50 93 / 10%), 0 5px 15px rgb(0 0 0 / 7%);
}

#submitBtn {
  background-color: rgb(84, 36, 185);
  color: white;
}

.fa-chevron-right {
  color: white;
  float: right;
}
.cv-container {
  color: #015c83;
}
.cv-header {
  background-color: #0171a1;
  color: #73b4cf;
}
.cv-header p {
  padding-left: 2em;
}

.dirty {
  border-color: #5a5;
  background: #efe;
}

.dirty:focus {
  outline-color: #8e8;
}

.error {
  border-color: red;
  background: #fdd;
}

.error:focus {
  outline-color: #f99;
}

.error-message {
  color: red;
  font-size: 0.5em;
}
</style>