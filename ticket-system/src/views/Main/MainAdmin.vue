<template>
  <v-container>
    <v-row justify="center">
      <v-tabs v-model="tab" color="deep-purple-accent-4" align-tabs="center">
        <v-tab :value="1">Активные тикеты</v-tab>
        <v-tab :value="2">Выполненые тикеты</v-tab>
      </v-tabs>
    </v-row>
    <v-window v-model="tab">
      <v-window-item :value="1">
        <br> <br>
        <v-container>
          <v-row>
            <div v-for=" item in tickets" >
              <TicketCard :ticket="item" v-show="item.status == 'UNDONE'">
              </TicketCard>
            </div>
          </v-row>
        </v-container>
      </v-window-item>
      <v-window-item :value="2">
        <br>
        <v-container>
          <v-row class="ticket-pos">
            <div v-for="item in tickets">
              <TicketCard :ticket="item" v-show="item.status == 'DONE'">
              </TicketCard>
            </div>

          </v-row>
        </v-container>
      </v-window-item>
    </v-window>
  </v-container>
</template>

<script>
import TicketCard from '../../components/Main/TicketCard.vue'

export default {
  name: 'MainAdmin',
  props: {
    ticket: Object
  },
  components: {
    TicketCard,
  },

  computed: {
    tickets() {
      return this.$store.state.ticket.tickets;
    },

  },

  data: () => ({
    tab: 1,
  }),
}
</script>