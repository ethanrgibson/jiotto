<script setup>
import { logger } from '@/utils/Logger.js';

let editableGuessData = ''

let secretWordData = ''

function chooseSecretWord() {
  logger.log(secretWordData)
}

function makeGuess() {
  if (editableGuessData === secretWordData) {
    logger.log('correct!')
  }
  else (logger.log('incorrect!'))
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
            <input v-model="editableGuessData" type="text" name="guess" id="userGuess" maxlength="5">
            <div class="text-end m-4">
              <button class="btn btn-purple" type="submit">Guess!</button>
            </div>
          </form>
        </div>
        <div class="text-center">
          Choose The Secret Word!
        </div>
        <div>
          <form @submit.prevent="chooseSecretWord()">
            <label for="guess">Your Word</label>
            <input v-model="secretWordData" type="text" name="guess" id="userGuess" maxlength="5">
            <div class="text-end m-4">
              <button class="btn btn-purple" type="submit">Submit</button>
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

label {
  display: block;
  text-align: center;
}
</style>
