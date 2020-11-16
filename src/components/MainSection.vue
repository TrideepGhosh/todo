<template>
    <div class="container">
        <div class="d-flex mx-5">
            <h1 class="mx-2">Today</h1>
            <div class="d-flex my-2">
                <p>{{ day }}</p>
                <p>{{ date }}</p>
                <p>{{ month }}</p>
            </div>

        </div>
        <div class="d-flex mx-5" v-if="show">
            <span class="material-icons mx-2" style="color:#DB4C3F" @click="TodoShow">add</span>
            <p>Add task</p>
        </div>
        <div class="d-flex mx-5" v-if="!show">
            <Todo @removed="TodoShow"/>
        </div>

    </div>
</template>

<script>
import Todo from './Todo'
export default {
  name: 'MainSection',
  components: {
    Todo
  },
  data () {
    return {
      day: null,
      month: null,
      date: null,
      show: true
    }
  },
  methods: {
    callFunction: function () {
      var currentDate = new Date()
      this.month = currentDate.toLocaleString('default', { month: 'short' })
      this.date = currentDate.getDate()
      const days = ['Sun', 'Mon', 'Tues', 'Wed', 'Thurs', 'Fri', 'Sat']
      this.day = days[currentDate.getDay()]
    },
    TodoShow () {
      this.show = !this.show
    }
  },
  mounted () {
    this.callFunction()
  }
}
</script>

<style scoped>
p{
    margin-right: 3px;
    color:rgb(161, 161, 161);
    font-size: 13px;
}
span{
        cursor: pointer;
    }
</style>
