<script setup>
import { logger } from '@/utils/Logger.js';
import { ref } from 'vue';

let editableGuessData = ref({
  guess: ''
})



function makeGuess() {
  logger.log('your guess is', editableGuessData.value)

}


</script>

<template>
  <div class="container-fluid home-container">
    <div class="row">
      <div class="col-12">
        <div class="text-center">
          Guess The Secret Word!
        </div>
        <div>
          <form @submit.prevent="makeGuess()">
            <label for="guess">Your Guess</label>
            <input v-model="editableGuessData.guess" type="text" name="guess" id="userGuess" maxlength="5">
            <div class="text-end m-4">
              <button class="btn btn-purple" type="submit">Guess!</button>
            </div>
          </form>
        </div>
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">
.home-container {
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}
</style>
