<template>
  <q-dialog
    :value="showTransaction"
    @input="$emit('update:showTransaction', $event)"
    confirm
  >
    <q-card>
      <q-card-section class="row items-center">
        <q-avatar
          icon="arrow_forward"
          color="primary"
          text-color="white"
          class="q-mr-sm"
        />
        <div class="text-h6 q-pa-sm">
          Transaction Sent
        </div>
      </q-card-section>
      <q-card-section>
        Transaction ID:
        <a
          :href="`${explorerUrl}/transaction/${transaction}`"
          target="_blank"
          style="word-wrap: break-word;"
        >
          {{ transaction }}
        </a>
      </q-card-section>
      <q-card-actions align="center">
        <q-btn class="hover-accent" label="Ok" color="primary" v-close-popup />
      </q-card-actions>
    </q-card>
  </q-dialog>
</template>

<script>
import { mapGetters } from "vuex";
export default {
  props: ["transaction", "showTransaction"],
  computed: {
    ...mapGetters("blockchains", ["currentChain"]),
    explorerUrl() {
      return this.currentChain.NETWORK_EXPLORER;
    }
  }
};
</script>
