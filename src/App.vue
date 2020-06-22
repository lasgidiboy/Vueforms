<template>
  <div class="container">
    <form action>
      <div class="row justify-content-md-center">
        <div class="col-md-7">
          <h1>File a Complaint</h1>
          <hr />
          <div class="form-group">
            <label for="email">Mail</label>
            <input
              type="text"
              id="email"
              class="form-control"
              :value="userData.email"
              @input="userData.email = $event.target.value"
            />
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <input
              type="password"
              id=""
              class="form-control"
              v-model="userData.password"
            />
          </div>
          <div class="form-group">
            <label for="age">Age</label>
            <input
              type="number"
              id="age"
              class="form-control"
              v-model="userData.age"
            />
          </div>
        </div>
      </div>
      <div class="row justify-content-md-center">
        <div class="col-md-7 form-group">
          <label for="message">Message</label>
          <br />
          <!-- Interpolation between <textarea>{{ test }}</textarea> doesn't work!-->
          <textarea
            id="message"
            rows="5"
            class="form-control"
            v-model="message"
          ></textarea>
        </div>
      </div>
      <div class="row justify-content-md-center">
        <div class="col-md-7">
          <div class="form-group">
            <label for="sendmail">
              <input
                type="checkbox"
                id="sendmail"
                value="SendMail"
                v-model="sendMail"
              />
              Send Mail
            </label>
            <label for="sendInfomail">
              <input
                type="checkbox"
                id="sendInfomail"
                value="SendInfoMail"
                v-model="sendMail"
              />
              Send Infomail
            </label>
          </div>
        </div>
      </div>
      <div class="row justify-content-md-center">
        <div class="col-md-7 form-group">
          <label for="male">
            <input type="radio" id="male" value="Male" v-model="gender" /> Male
          </label>
          <label for="female">
            <input type="radio" id="female" value="Female" v-model="gender" />
            Female
          </label>
        </div>
      </div>
      <div class="row justify-content-md-center">
        <div class="col-md-7 from-group">
          <label for="priority">Priority</label>
          <select id="priority" class="form-control" v-model="seletedPriority">
            <option
              v-for="(priority, index) in priorities"
              :key="index"
              :selected="priority == 'female'"
              >{{ priority }}</option
            >
          </select>
        </div>
      </div>
      <div class="row">
        <div class="col-md-6 col-md-offest-3">
        <app-switch v-model="dataSwitch"></app-switch>
        </div>
      </div>
      <hr />
      <div class="row justify-content-md-center">
        <div class="col-md-7">
          <button class="btn btn-primary" @click.prevent="Submitted">Submit!</button>
        </div>
      </div>
    </form>
    <hr />
    <div class="row justify-content-md-center" v-if="isSubmitted">
      <div class="col-md-7">
        <div class="card mb-4">
          <div class="card-header">
            <h4>Your Data</h4>
          </div>
          <div class="card-body">
            <p>Mail: {{ userData.email }}</p>
            <p>Password: {{ userData.password }}</p>
            <p>Age: {{ userData.age }}</p>
            <p style="white-space: pre">Message:{{ message }}</p>
            <p>
              <strong>Send Mail?</strong>
            </p>
            <ul>
              <li v-for="(item, index) in sendMail" :key="index">{{ item }}</li>
            </ul>
            <p>Gender: {{ gender }}</p>
            <p>Priority:{{ seletedPriority }}</p>
            <p>Switched:{{dataSwitch}}</p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Switch from "./switch.vue";
export default {
  data() {
    return {
      userData: {
        email: "",
        password: "",
        age: 27
      },
      message: "the message",
      sendMail: [],
      gender: "",
      priorities: ["male", "female", "man"],
      seletedPriority: "man",
      dataSwitch: true,
      isSubmitted:false
    };
  },
  methods: {
    Submitted(){
      this.isSubmitted = true
    }
  },
  components: {
    appSwitch: Switch
  }
};
</script>

<style></style>
