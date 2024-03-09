<template>
  <v-card variant="outlined" class="mx-auto" width="250"
    :color="ticket.priority == 'HIGH' ? 'red' : ticket.priority == 'MED' ? 'orange' : 'grey'">
    <v-card-item>
      <div>
        <div class="text-overline mb-1">
          {{ ticket.from }}
        </div>
        <div class="text-h6 mb-1">
          {{ ticket.summary }}
        </div>
        <div class="text-caption ticket_content">{{ ticket.content }}</div>
      </div>
      <div class="text-caption ticket_content">{{ ticket.priority }}</div>


    </v-card-item>
    <v-card-actions>
      <v-btn v-if="user.role == 'user'" @click="TicketDel" color="red" block class="mt-2">Удалить тикет</v-btn>
      <v-btn v-if="user.role == 'admin'" @click="TicketOtvet" color="bleck" block class="mt-2">Ответить на
        тикет</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script>
export default {
  props: {
    ticket: Object

  },

  methods: {
    TicketDel() {
      this.$store.commit('DELETE_TICKET', { id: this.ticket.id });
    },

  },
  computed: {
    user() {
      return this.$store.state.user.curUser;
    },
  }

}

</script>

<style>
.ticket_content {
  white-space: nowrap;
  /* Текст не переносится */
  overflow: hidden;
  /* Обрезаем всё за пределами блока */
  text-overflow: ellipsis;
  /* Добавляем многоточие */
}
</style>