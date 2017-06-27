<template>
<div>
  <p>
    Here is the demo of vue-fullcalendar, no jquery fullcalendar.js required!
    <button type="button" @click="addMonth">+</button>
  </p>
  <full-calendar class="test-fc" :events="fcEvents" first-day='1' locale="fr" v-for="month in months" :key="month" :currentMonth="month" @changeMonth="changeMonth" @eventClick="eventClick" @dayClick="dayClick" @moreClick="moreClick">
    <slot name="fc-header-left">
    </slot>
  </full-calendar>
</div>
</template>
<script>
import moment from 'moment'

let demoEvents = [{
    title: 'Sunny 725-727',
    start: '2017-05-25',
    end: '2017-06-27',
    cssClass: 'family'
  },
  {
    title: 'Lunfel 726-727',
    start: '2017-02-26',
    end: '2017-02-27',
    cssClass: ['home', 'work']
  },
  {
    title: 'Lunfel 2/27-2/28',
    start: '2017-02-27',
    end: '2017-02-28'
  },
  {
    title: 'Lunfel 2/27-2/28',
    start: '2017-02-27',
    end: '2017-02-28'
  },
  {
    title: 'Lunfel 2/27-2/28',
    start: '2017-02-27',
    end: '2017-02-28'
  },
  {
    title: 'Lunfel 2/26-3/05',
    start: '2017-02-26',
    end: '2017-03-05'
  },
  {
    title: 'Lunfel 1/27-1/28',
    start: '2017-01-27',
    end: '2017-01-28'
  },
  {
    title: 'Lunfel 1/27-2/2',
    start: '2017-01-27',
    end: '2017-02-02'
  },
  {
    title: 'Lunfel 3/27-3/28',
    start: '2017-03-27',
    end: '2017-03-28'
  },
  {
    title: 'Lunfel 5/18-5/29',
    start: '2017-05-18T23:55:00-04:00',
    end: '2017-05-29T01:15:00-04:00'
  },
];


export default {
  data() {
    return {
      name: 'Sunny!',
      fcEvents: demoEvents,
      months: [
        moment('2017-05-01'),
        moment('2017-06-01')
      ]
    }
  },
  methods: {
    addMonth: function addMonth() {
      this.months.push(moment('2017-07-01'))
    },
    'changeMonth' (start, end, current) {
      console.log('changeMonth', start.format(), end.format(), current.format())
    },
    'eventClick' (event, jsEvent, pos) {
      console.log('eventClick', event, jsEvent, pos)
    },
    'dayClick' (day, jsEvent) {
      console.log('dayClick', day, jsEvent)
    },
    'moreClick' (day, events, jsEvent) {
      console.log('moreCLick', day, events, jsEvent)
    }
  },
  components: {
    'full-calendar': require('src/fullCalendar')
  }
}
</script>
<style lang='scss'>
.app {
    color: green;
}
</style>
