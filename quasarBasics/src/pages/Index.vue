<template>
  <q-page padding>
    <button class="pos-button" 
      @click="counter++">
        {{counter}}
    </button>
    <!-- mouseenter -->
    <input 
      v-model="message"
     @keyup.enter="alertMessage"
     @keyup.esc="clearMessage"
     v-autofocuses
     v-bind:class="{'error':message.length>22}"
     ref="messageInput"
     />
    <button @click="clearMessage">Clear</button>
    <!-- v-if and v-show -->
    <h5 
      class="border-gray" 
      v-if="message.length"
    >{{message}}</h5>
    <h6
      v-else
    >No message</h6>

    <hr>

    <p>Upper Case: {{uppercase}}</p>
    <p>Lower Case: {{message | lowerCase }}</p>
  </q-page>
</template>

<script>
export default {
   data() {
     return {
       message: 'You loaded this page on ' + new Date().toLocaleString(),
       counter: 0
     }
  },
  computed: {
    uppercase() {
      return this.message.toUpperCase();
    },
  },
  methods: {
    clearMessage() {
      this.message = '';
    },
    handleKeyup(e) {
      console.log(e);
      if(e.keyCode == 27){
        this.clearMessage()
      }else if(e.keyCode == 13){
        this.alertMessage()
      }
    },
    alertMessage() {
      alert(this.message)
    }
  },
  filters: {
    lowerCase(value) {
      return value.toLowerCase()
    }
  },
  directives: {
    autofocuses: {
      inserted(el) {
        el.focus()
      }
    }
  },
  // beforeCreate() {
  //   console.log('beforeCreate');
  // },
  // created() {
  //   console.log('created');
  // },
  // beforeMount() {
  //   console.log('beforeMount');
  // },
  mounted() {
    console.log(this.$refs);
    this.$refs.messageInput.className = 'bg-green'
  },
  // beforeUpdate() {
  //   console.log('beforeUpdate');
  // },
  // updated() {
  //    console.log('updated');
  // },
  // beforeDestroy() {
  //   console.log('beforeDestroyed');
  // },
  // destroyed() {
  //   console.log('destroyed');
  // }

}
</script>

<style>
  .border-gray {
    border: 1px solid gray;
  }
  .pos-button {
    position: absolute;
    right: 10px;
  }
  .error {
    background: red;
  }
</style>
