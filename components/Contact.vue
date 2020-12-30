<template>
  <div class="row">
    <div class="col-lg-8 col-lg-offset-2 col-sm-12 col-md-10 col-md-offset-1">
      <form novalidate="novalidate" @submit="formSubmit" class="contactFrom" id="contactForm">
        <div class="row">
          <div class="col-lg-6 col-sm-6">
            <input class="input-form required" type="text" name="l_name" id="l_name" placeholder="Name">
          </div>
          <div class="col-lg-6 col-sm-6">
            <input class="input-form required" type="email" name="email" id="email" placeholder="Email Address">
          </div>
          <div class="col-lg-12 col-sm-12">
            <textarea class="input-form required" name="con_message" id="con_message" v-model="formMsg" placeholder="Write Message"></textarea>
          </div>
        </div>
        <button class="common_btn red_bg" type="submit" id="con_submit"><span>Send Message</span></button>
      </form>
    </div>
  </div>
</template>

<script>
import axios from 'axios';
    export default {
      data() {
        return {
          formMsg: ''
        }
      },
      methods: {
        formSubmit(e) {
          e.preventDefault()
          const formData = new FormData()
          const dat = {
            'textarea-159': this.formMsg,
            // more fields
          }
          for (const name in dat) {
            formData.append(name, dat[name])
          }
          axios({
       method: 'post',
       url: 'https://wordpress.gintonic.cf/wp-json/wp/v2/wpcf7_contact_form/159',
       data: formData,
       headers: { 'Content-Type': 'multipart/form-data' },
     })
       .then((response) => {
         console.log(response.data.message) // throw that in a <div> and you’re done!
       })
       .catch((error) => {
         // internet connection error
       })

          // more steps!
        }
      }
    }
</script>

<style scoped>
  .row {
  margin-left: -20px;
  *zoom: 1;
}

.row:before,
.row:after {
  display: table;
  line-height: 0;
  content: "";
}

.row:after {
  clear: both;
}

</style>
