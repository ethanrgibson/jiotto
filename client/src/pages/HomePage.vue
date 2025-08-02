<script setup>
import { logger } from '@/utils/Logger.js';
import { ref } from 'vue'


let editableGuessData = ref('')
let secretWordData = ref('')
let match = ref(null)



function chooseSecretWord() {
  logger.log(secretWordData.value)
}

function makeGuess() {
  if (editableGuessData.value == '')
    return
  if (editableGuessData.value === secretWordData.value) {
    logger.log('correct!')
    match.value = true
  }
  else {
    logger.log('incorrect!')
    match.value = false
  }
}


</script>

<template>
  <div class="container-fluid home-container">
    <div class="row">
      <div class="col-12">
        <div class="text-center">
          Choose The Secret Word!
        </div>
        <div>
          <form @submit.prevent="chooseSecretWord()">
            <label for="guess">Your Word</label>
            <input v-model="secretWordData" type="text" name="guess" id="userGuess" maxlength="5">
            <div class="text-center m-4">
              <button class="btn btn-purple" type="submit">Submit</button>
            </div>
          </form>
        </div>
        <div class="text-center">
          Guess The Secret Word!
        </div>
        <div>
          <form @submit.prevent="makeGuess()">
            <label for="guess">Your Guess</label>
            <input v-model="editableGuessData" type="text" name="guess" id="userGuess" maxlength="5">
            <div class="text-center m-4">
              <button class="btn btn-purple" type="submit">Guess!</button>
            </div>
          </form>
        </div>
        <div :style="{ backgroundColor: match ? 'green' : 'red' }">
          <div>
            <div class="display-5 text-center text-white">
              {{ match ? 'Correct!' : 'Incorrect!' }}
            </div>
          </div>
        </div>
      </div>
    </div>
  </div>

  <div style="background-image: url(); background-repeat: no-repeat; width: fit-content; border-radius: 16px; font-size: 24px;">
<span>  <p> </p></span>
  </div>
</template>

<style scoped lang="scss">
.home-container {
  flex-grow: 1;
  display: flex;
  justify-content: center;
  align-items: center;
}

label {
  display: block;
  text-align: center;
}


</style>
