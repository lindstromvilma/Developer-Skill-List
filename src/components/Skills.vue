<template>
  <div class="hello">
    <div class="holder">

      <form @submit.prevent="addSkill">
        <input type="text" autocomplete="off" placeholder="Enter here a skill you have..." v-model="skill" v-validate="'min:5'" name="skill">

        <transition name="alert-in" enter-active-class="animated bounceIn" leave-active-class="animated fadeOut">
        <p class="alert" v-if="errors.has('skill')">{{ errors.first('skill') }}</p>
        </transition>
      </form>

      <ul>
        <transition-group name="list" enter-active-class="animated bounceInUp" leave-active-class="animated fadeOutDown">
          <li v-for="(data, index) in skills" :key='index'>
            {{ data.skill }}
            <i class="fa fa-remove" v-on:click="remove(index)"></i>
          </li>
        </transition-group>
      </ul>

      <p>These are the skills that you posess.</p>
    </div>
  </div>
</template>

<script>
export default {
  name: 'Skills',
  data() {
    return {
      skill: '',
      skills: [
        { "skill": "Vue.js" },
        { "skill": "Frontend Developer" }
      ]
    }
  },
  methods: {
    addSkill() {
      this.$validator.validateAll().then((result) => {
        if (result) {
          this.skills.push({skill: this.skill})
          this.skill = '';
        } else
        console.log('Not valid');
      })
    },
    remove(id) {
      this.skills.splice(id,1)
    }
  }
}
</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped>
@import "https://cdn.jsdelivr.net/npm/animate.css@3.5.1";
@import "https://maxcdn.bootstrapcdn.com/font-awesome/4.7.0/css/font-awesome.min.css";

.holder {
  background: #ccd0d8;
}

ul {
  margin: 0;
  padding: 0;
  list-style-type: none;
}

ul li {
  padding: 20px;
  font-size: 1.3em;
  background-color: #6AB74F;
  border-left: 6px solid #38B179;
  margin-bottom: 3px;
  color: #212329;
}

p {
  text-align: center;
  padding: 50px 0 40px;
  margin: 0;
  color: #373738;
}

.container {
  box-shadow: 0px 0px 40px #ccd0d8;
}

input {
  width: calc(100% - 40px);
  border: 0;
  padding: 20px;
  margin-bottom: 3px;
  font-size: 1em;
  background-color: #212329;
  color: #a0a0a0;
}
input:focus {
  outline: none;
  font-size: 1.3em;
}

.alert {
  background: #ccd0d8;
  font-weight: bold;
  display: inline-block;
  padding: 5px;
  margin: 5px;
}

.alert-in-enter-active {
  animation: bounce-in .5s;
}
.alert-in-leave-active {
  animation: bounce-in .5s reverse;
}

@keyframes bounce-in {
  0% {
    transform: scale(0);
  }
  50% {
    transform: scale(1.2);
  }
  100% {
    transform: scale(1);
  }
}

i {
  float: right;
  cursor: pointer;
  font-size: 25px;
}

</style>
