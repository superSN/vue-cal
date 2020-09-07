<template lang="pug">
//- This is an isolated test view. Just for testing purpose.
div.test-view
  vue-cal.ml-2.mr-1(
    :events="events"
    :time="false"
    :todayButton='true'
    :events-on-month-view="'short'"
    :disable-views="['years', 'year', 'day']"
    sticky-split-labels
    locale="zh-cn"
    :on-event-click="() => (clicksCount++)")
  p clicks: {{clicksCount}}
</template>

<script>
import VueCal from '@/vue-cal'

const now = new Date()

export default {
  components: { VueCal },
  data: () => ({
    clicksCount: 0,
    selectedDate: now,
    view: 'week',
    events: [
      {
        start: new Date(new Date(now).setHours(1, 0, 0)),
        end: new Date(new Date(now).setHours(4, 0, 0)),
        allDay: true,
        title: 'Event 1',
        split: 2
      },
      {
        start: new Date(new Date(now).setHours(1, 0, 0)),
        end: new Date(new Date(now).setHours(4, 0, 0)),
        title: 'Event 2',
        split: 1
      },
      {
        start: new Date(new Date(now).setHours(3, 0, 0)),
        end: new Date(new Date(now).setHours(5, 0, 0)),
        title: 'Event 3',
        split: 2
      }
    ],
    daySplits: [
      { label: 'Tom', color: 'green' },
      { label: 'Kate', color: 'pink' }
    ]
  }),

  methods: {
    log (...params) {
      // eslint-disable-next-line
      console.log(...params)
    }
  }
}
</script>

<style lang="scss">
.vuecal {}
.vuecal__event {
  background-color:#FAFAFA;
  border: 1px solid #EDEEEE;
}

// Global.
html, body, #app, .v-application--wrap, .container {height: 100%;}
#app {padding-top: 2em;}
.v-application--wrap {min-height: 0;padding-top: 7em;}
.test-view {
  height: 100%;
  overflow: auto;
  display: flex;
  flex-direction: column;
}
footer {display: none !important;}
</style>
