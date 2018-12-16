<template>
  <div class="container">
    <form>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <h1>File a Complaint</h1>
          <hr>
          <div class="form-group">
            <label for="email">eMail</label>
            <!-- two way data binding with v-model -->
            <input type="text" id="email" class="form-control" v-model.trim="userData.email">
          </div>
          <div class="form-group">
            <label for="password">Password</label>
            <!-- lazy modifier will only bind data when we leave the input -->
            <input type="password" id="password" class="form-control" v-model.lazy.trim="userData.password">
          </div>
          <div class="form-group">
            <label for="age">Age</label>
            <input type="number" id="age" class="form-control" v-model.number="userData.age">
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <label for="message">Message</label>
          <br>
          <!-- Interpolation between <textarea>{{ test }}</textarea> doesn't work!-->
          <textarea id="message" rows="5" class="form-control" v-model="message"></textarea>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <div class="form-group">
            <label for="sendmail">
              <input type="checkbox" id="sendmail" value="SendMail" v-model="sendMail"> Send Mail
            </label>
            <label for="sendInfomail">
              <input type="checkbox" id="sendInfomail" value="SendInfoMail" v-model="sendMail"> Send Infomail
            </label>
          </div>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 form-group">
          <label for="male">
              <!-- adding v-model binding to the same data will group radio buttons together -->
            <input type="radio" id="male" value="Male" v-model="gender"> Male
          </label>
          <label for="female">
            <input type="radio" id="female" value="Female" v-model="gender"> Female
          </label>
        </div>
      </div>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 from-group">
          <label for="priority">Priority</label>
          <!-- bind to the selectbox, this will bind the selected option -->
          <select id="priority" class="form-control" v-model="priority">
            <option v-for="p in priorities"> {{p}} </option>
          </select>
        </div>
      </div>
      <div class="row">
          <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3 from-group">
              <app-switch v-model="dataSwitch"></app-switch>
          </div>
      </div>
      <hr>
      <div class="row">
        <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
          <button class="btn btn-primary" @click.prevent="submitted">Submit</button>
        </div>
      </div>
    </form>
    <hr>
    <div class="row" v-if="isSubmitted">
      <div class="col-xs-12 col-sm-8 col-sm-offset-2 col-md-6 col-md-offset-3">
        <div class="panel panel-default">
          <div class="panel-heading">
            <h4>Your Data</h4>
          </div>
          <div class="panel-body">
            <p>eMail: {{ userData.email }} </p>
            <p>Password: {{ userData.password }} </p>
            <p>Age: {{ userData.age }} </p>
            <!-- set white=space to pre so it will save line breaks -->
            <p style="white-space: pre;">Message: {{ message }} </p>
            <p>
              <strong>Send Mail?</strong>
            </p>
            <ul>
              <li v-for="mailCheck in sendMail"> {{ mailCheck }} </li>
            </ul>
            <p>Gender: {{ gender }} </p>
            <p>Priority: {{ priority }} </p>
            <p>Switched: {{ dataSwitch }} </p>
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
import Switch from './Switch.vue';
export default {    
    data () {
        return {
            userData: {
                email: '',
                password: '',
                age: ''
            },
            message: 'Let us know what happened.',
            sendMail: [],
            gender: 'Male',
            priorities: ['High', 'Medium', 'Low'],
            priority: 'Medium',
            dataSwitch: true,
            isSubmitted: false
        }
    },
    components: {
        appSwitch: Switch
    },
    methods: {
        submitted() {
            this.isSubmitted = true
        }
    }
}
</script>

<style>
</style>
