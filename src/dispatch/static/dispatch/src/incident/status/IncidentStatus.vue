<template>
  <div>
    <div v-if="status == 'Active'">
      <v-badge bordered color="error" slot="activator" dot left offset-x="-10" offset-y="12">
        {{ status }}
      </v-badge>
      <v-tooltip bottom>
        <template #activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on" @click.stop="joinIncident(id)">
            <v-icon> mdi-account-plus </v-icon>
          </v-btn>
        </template>
        <span>Join</span>
      </v-tooltip>
      <v-tooltip bottom>
        <template #activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on" @click.stop="subscribeToIncident(id)">
            <v-icon> mdi-email-plus </v-icon>
          </v-btn>
        </template>
        <span>Subscribe</span>
      </v-tooltip>
    </div>
    <div v-if="status == 'Stable'">
      <v-badge bordered color="warning" slot="activator" dot left offset-x="-10" offset-y="12">
        {{ status }}
      </v-badge>
      <v-tooltip bottom>
        <template #activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on" @click.stop="joinIncident(id)">
            <v-icon> mdi-account-plus </v-icon>
          </v-btn>
        </template>
        <span>Join</span>
      </v-tooltip>
      <v-tooltip bottom>
        <template #activator="{ on, attrs }">
          <v-btn icon v-bind="attrs" v-on="on" @click.stop="subscribeToIncident(id)">
            <v-icon> mdi-email-plus </v-icon>
          </v-btn>
        </template>
        <span>Subscribe</span>
      </v-tooltip>
    </div>
    <div v-if="status == 'Closed'">
      <v-badge bordered color="success" dot left offset-x="-10" offset-y="12">
        {{ status }}
      </v-badge>
    </div>
  </div>
</template>

<script>
import { mapActions } from "vuex"

export default {
  name: "IncidentStatus",

  props: {
    status: {
      type: String,
      required: true,
    },
    id: {
      type: Number,
      required: true,
    },
  },

  methods: {
    ...mapActions("incident", ["joinIncident", "subscribeToIncident"]),
  },
}
</script>
