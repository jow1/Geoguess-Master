<template>
  <v-card color="#E1F5FE">
    <v-card-title>
      <span>Set a number of rounds.</span>
    </v-card-title>
    <v-card-text>
      <v-container>
        <v-row>
          <v-col 
            cols="6"
            sm="4"
            md="4"
            lg="4"
            xl="4">
            <v-text-field 
              v-model.number="state.numberOfRounds" 
               type="number"
               min=1
               max=10 >
            </v-text-field>
          </v-col>          
        </v-row>
      </v-container>
    </v-card-text>
    <v-card-actions>
      <div class="flex-grow-1"></div>
      <v-btn
        dark
        depressed
        color="#43B581"
        @click="setRoomRounds">NEXT</v-btn>
      <v-btn
        dark
        depressed
        color="#FF5252"
        @click="cancel">CANCEL</v-btn>
    </v-card-actions>
  </v-card>
</template>

<script lang="ts">
import { defineComponent, reactive, } from '@vue/composition-api'

export default defineComponent({
  
  setup(props, context) {

    const state = reactive<{
      numberOfRounds: number,
    }>({
      numberOfRounds: 5,
    })

    function setRoomRounds(): void {
      context.emit('setRoomRounds', state.numberOfRounds)
    }

    function cancel(): void {
      context.emit('cancel')
    }

    return {
      state,
      setRoomRounds,
      cancel,
    }
  }
})
</script>

<style scoped>

</style>