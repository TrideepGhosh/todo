<template>
  <div class="container">
        <div class="d-flex flex-column mx-3 TodoDiv">
            <div class="d-flex">
                <input type="text" placeholder="New Todo" class="mx-3 my-4" v-model="Todo" @change="active">
                <span class="material-icons my-4" style="color: rgb(128, 128, 128);" v-bind:class="{ isActive:addTodo }">check</span>
            </div>
            <div class="d-flex">
                <Datepicker style="width:150px" class="mx-3" :value.sync="date" :calendar-config="getCalendarConfig()" :select-mode="mode" :key="mode" ref="datepickerExample"/>
                <span class="material-icons my-2" @click="remove" style="color:#DB4C3F">remove_circle_outline</span>
            </div>

       </div>

    </div>
</template>

<script>
import { Datepicker } from '@e9ine/vue_components'
export default {
  name: 'Todo',
  data () {
    return {
      date: new Date(),
      mode: 'day',
      Todo: null,
      isActive: false
    }
  },
  components: {
    Datepicker
  },
  methods: {
    remove () {
      this.$emit('removed', true)
    },
    active () {
      if (this.Todo !== '' || this.Todo !== null) {
        this.isActive = true
      }
      this.isActive = false
    },
    getCalendarConfig () {
      return {
        dateFormat: 'd/m/Y',
        altFormat: 'd/m/Y',
        altInput: true,
        weekNumbers: false
      }
    },
    calendarOpened () {
      this.$refs.datepickerExample.setDate('2021;07-10', false, 'Y-m-d')
    }
  }
}
</script>

<style scoped>
    input{
        width: 80%;
        border: none;
        border-bottom:1px solid lightgrey;
        background: transparent;
    }
    ::placeholder{
        padding: 30px;
        color: rgb(128, 128, 128);
        opacity: 1;
    }
    input:focus{
        outline: none;
    }
    input[type=text]{
        padding-left: 30px;
        color: rgb(128, 128, 128);
    }
    .TodoDiv{
        border:1px solid lightgray;
        border-radius: 10px;
        height: 150px;
    }
    span{
        cursor: pointer;
    }
    .addTodo{
        color: rgb(51, 185, 51) !important;
    }
</style>
