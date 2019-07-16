<template>
  <div id="app">
    <div id="nav">
      <router-link to="/">Home</router-link> |
      <router-link to="/about">About</router-link>
    </div>
    <router-view/>
    <h1 class="text-center app-title">
   {{ $t('msg') }}
</h1>   
<!-- <a-divider>{{ $t('title') }}</a-divider> -->
<a-divider>{{ $tc('button',2) }}</a-divider>
    <button
    v-for="entry in languages"
    :key="entry.title"
    @click="changeLocale(entry.language)"
  >{{entry.title}}</button>

  <h1 class="text-center app-title">
    <p v-t="{path:'msg', locale:'en', args:{form:'KKDay'}}"></p>
  </h1>
  <p v-t="'local'"></p>
  </div>
 
</template>
<script>
import i18n from '@/plugins/i18n';

export default {
 beforeCreate () {
    this.form = this.$form.createForm(this);
  },
name: 'App',
  data() {  
    
    return {        
      languages: [            
        { language: 'en', title: 'English' },            
        { language: 'vi', title: 'Vietnamese' }        
      ]    
    };
  },
  methods: {
    changeLocale(locale){
      i18n.locale = locale;
    },
     handleSubmit (e) {
      e.preventDefault();
      this.form.validateFields((err, values) => {
        if (!err) {
          console.log('Received values of form: ', values);
        }
      });
    },
  },
  
};
</script>


<style>
#app {
  font-family: 'Avenir', Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
}
#nav {
  padding: 30px;
}

#nav a {
  font-weight: bold;
  color: #2c3e50;
}

#nav a.router-link-exact-active {
  color: #42b983;
}
#components-form-demo-normal-login .login-form {
  max-width: 300px;
}
#components-form-demo-normal-login .login-form-forgot {
  float: right;
}
#components-form-demo-normal-login .login-form-button {
  width: 100%;
}
</style>
