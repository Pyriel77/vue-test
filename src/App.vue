<template>
  <div id="app">
    <div class="overlay">
      <button @click="toggleOverlay" class="toggle-button">
        Toggle Overlay
      </button>
      <div v-if="overlayVisible" class="overlay-content">
        <div class="event-details">
          <div class="event-name">{{ currentEvent.name }}</div>
          <div class="event-date">
            {{ currentEvent.from }} - {{ currentEvent.to }}
          </div>
          <div
            v-for="(talent, index) in currentEvent.talent"
            :key="index"
            class="event-talent"
          >
            {{ talent }}
          </div>
        </div>
      </div>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      overlayVisible: false,
      currentEvent: {},
      eventData: [
        {
          name: 'FGC',
          from: '2020-03-10',
          to: '2020-03-12',
          color: '#00d487',
          talent: ['LD'],
        },
        {
          name: 'Rocket League Showdown 2020 Summer Shuffle',
          from: '2020-06-29',
          to: '2020-07-12',
          color: '#e5043b',
          talent: ['EterNaLeNvy', 'DakotaCox', 'Sarah Jessica Parker'],
        },
        {
          name: 'Dota Summit',
          from: '2020-11-02',
          to: '2020-11-07',
          color: '#ca6412',
          talent: ['HMW', 'Phil'],
        },
      ],
    };
  },
  methods: {
    toggleOverlay() {
      console.log(this.overlayVisible);
      this.overlayVisible = !this.overlayVisible;
      if (this.overlayVisible) {
        const randomIndex = Math.floor(Math.random() * this.eventData.length);
        this.currentEvent = this.eventData[randomIndex];
      } else {
        this.currentEvent = {};
      }
    },
  },
};
</script>

<style></style>
