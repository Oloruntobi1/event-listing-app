
<template>
      <div>
        <h1>Events</h1>
        <EventCard
          v-for="(event, index) in events"
          :key="index"
          :event="event"
          :data-index="index"
        />
      </div>
    </template>
  <!-- <div class="container">
    <div>
      <logo />
      <h1 class="title">
        my-second-nuxt-app
      </h1>
      <h2 class="subtitle">
        My awe-inspiring Nuxt.js project
      </h2> -->
      <!-- <div class="links">
        <a
          href="https://nuxtjs.org/"
          target="_blank"
          class="button--green"
        >
          Documentation
        </a>
        <a
          href="https://github.com/nuxt/nuxt.js"
          target="_blank"
          class="button--grey"
        >
          GitHub
        </a>
      </div> -->
    <!-- </div>
  </div> -->


<script>
  import EventCard from '@/components/EventCard.vue'
   import { mapState } from 'vuex'
    export default {
      head() { 
        return {
          title: 'Event Listing'
            }
            },
         async fetch({ store, error }) {
        try {
          await store.dispatch('events/fetchEvents')
        } catch (e) { 
          error({
            statusCode: 503,
            message: 'Unable to fetch events events at this time'
          })
        
        }
        },
            
        computed: mapState({
        events: state => state.events.events
      }),
      components: {
        EventCard
      }
        }
  
  
    </script>

<style>
.container {
  margin: 0 auto;
  min-height: 100vh;
  display: flex;
  justify-content: center;
  align-items: center;
  text-align: center;
}

.title {
  font-family: 'Quicksand', 'Source Sans Pro', -apple-system, BlinkMacSystemFont,
    'Segoe UI', Roboto, 'Helvetica Neue', Arial, sans-serif;
  display: block;
  font-weight: 300;
  font-size: 100px;
  color: #35495e;
  letter-spacing: 1px;
}

.subtitle {
  font-weight: 300;
  font-size: 42px;
  color: #526488;
  word-spacing: 5px;
  padding-bottom: 15px;
}

.links {
  padding-top: 15px;
}
</style>
