<template src="./Index.html"></template>
<script>
  import { mapGetters } from 'vuex'
  import RideForm from './New.vue'

  export default {
    data(){
      return {
        clicked: false
      }
    },
    created() {
      this.$store.dispatch('ride/fetchRides')
    },
    methods: {
      toggleButton(){
        this.clicked = !this.clicked
      },
      deleteRide(index, id){
        this.$store.dispatch('ride/deleteRide', { index: index, id: id });
      }
    },
    computed: {
      ...mapGetters('ride',[
          'rides',
          'weeklyTotals'
      ]),
      btnText(){
        return this.clicked ? 'Cancel' : 'New ride'
      }
    },
    components: {
      RideForm
    }
  }
</script>
<style scoped>
  .header {
    height: 56px;
    display: flex;
    flex-flow: row;
    justify-content: space-between;
    align-items: center;
    padding: 10 20px;
  }

  #heading {
    display: inline-block;
    width: 200px;
    margin-top: 10px;
    padding: 10px;
  }

  .newRideBtn {
    border: 1px solid #521751;
    color: #521751;
    padding: 10px 20px;
    font: inherit;
    cursor: pointer;
    border-radius: 3px;
    width: 106px;
  }

  .newRideBtn:hover {
    background-color: #521751;
    color: white;
  }

  .close span {
    color: red;
  }

  .box-content {
    display: inline-block;
    width: 200px;
    padding: 10px;
  }

  .bottom {
    border-bottom: 1px solid #ccc;
  }

  .right {
    border-right: 1px solid #ccc;
  }

  .trash-icon {
    color: darkred;
    cursor: pointer;
  }
</style>