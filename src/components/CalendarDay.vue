<template>
    <!--Tage-->
              <div 
              class="card"
              :class="[day.active ? activeBorderClass : '']"
              >
                <div class="card-header text-center bg-vue"
                :class="[day.active ? activeClass : defaultClass]"
                style="cursor: pointer;"
                @click="setActiveDay(day.id)"
                >
                  <strong> {{ day.fullName }} </strong>
                </div>
                <div class="card-body">
                  <div>{{ day.id }}</div>

                  <CalendarEvent 
                    v-for="(event, index) in day.events"
                    :key="index"
                    :event="event"
                    :day="day"
                    />

                  

                </div>
              </div>
</template>

<script>

import { store } from '../store.js';
import CalendarEvent from './CalendarEvent';

export default {
    name: 'CalendarDay',
    props: ['day'],
    data() {
      return {
      defaultClass: 'bg-vue',
      activeClass: 'bg-vue2',
      activeBorderClass: 'border-color-vue2'
      }
    },
    components: {
      CalendarEvent
    },
    methods: {
      setActiveDay(dayId) {
        store.setActiveDay(dayId);
      }
    }
}
</script>

<style scoped>
 .bg-vue {
    background-color: rgb(52, 73, 94);
    color: white;
  }
  .bg-vue2 {
    background-color: rgb(65, 184, 131);
    color: white;
  }
  .border-color-vue2 {
    border-color:rgb(65, 184, 131);
    border-width: 3px;
  }

</style>