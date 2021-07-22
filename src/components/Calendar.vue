<template>
  <div>
    <h1>Calendar</h1>
    <p>events:</p>
    <p>{{ events }}</p>
    <button type="submit" @click="fetchEvents()">fetchEvents</button>
  </div>
</template>

<script>
import axios from 'axios';

export default {
  name: 'Calendar',
  data: () => ({
    events: [],
  }),
  methods: {
    fetchEvents() {
      axios
        .get('https://86d9328a09f44ac1b10512d679c2c0db.vfs.cloud9.ap-northeast-1.amazonaws.com/events')
        .then((response) => {
          this.events = response.data;
        })
        .catch((error) => {
          console.error(error);
        });
    },
  },
};
</script>

