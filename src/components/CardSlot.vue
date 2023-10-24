<template>
  <div class="text-center q-pa-sm">
    <q-card class="my-card bg-secondary text-white">
      <q-card-section>
        <div class="text-h6">
          <slot name="card-header"></slot>
        </div>
      </q-card-section>

      <q-card-section>
        <slot name="card-content"></slot>
      </q-card-section>

      <q-separator dark />

      <q-card-actions>
        <slot name="card-footer" align="center"></slot>
      </q-card-actions>
    </q-card>
  </div>
</template>
<script>
import { defineComponent } from "vue";

export default defineComponent({});
</script>
