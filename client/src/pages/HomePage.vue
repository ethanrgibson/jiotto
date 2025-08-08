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

  <div class="cardContainer">
    <div class="cardBackground">
      <div class="cardContent">
        <div>
          <img class="numberIcon"
            src="https://safeut.utahhealth.acsitefactory.com/sites/g/files/zrelqx271/files/media/images/2025/numberoneicon.png"
            alt="Number 1">
        </div>
        <div>
          <b style="font-size: 32px;">
            Find the right place.
          </b>
        </div>
        <div>
          <p style="font-size: 20px;">
            It's best to talk somewhere comfortable and private where you won’t be constantly interrupted. If it’s
            hard
            to
            find privacy, try to invite them to go on a walk with you.
          </p>
        </div>
      </div>
      <div>
        <img src="https://safeut.utahhealth.acsitefactory.com/sites/g/files/zrelqx271/files/media/images/2025/image.png"
          class="cardImage">
      </div>
    </div>
  </div>
</template>

<style scoped lang="scss">


.cardContainer {
  display: flex;
}

.cardBackground {
  display: flex;
  background-image: url(https://safeut.utahhealth.acsitefactory.com/sites/g/files/zrelqx271/files/media/images/2025/carousel.png);
  background-repeat: no-repeat;
  width: 1083px;
}

.cardContent {
  display: flex;
  flex-direction: column;
  flex-grow: 1;
  justify-content: center;
  padding: 35px;
  gap: 1rem;
}

.numberIcon {
  width: 42px;
  aspect-ratio: 1;
}

.cardImage {
  width: 445.1;
  height: 512px;
}






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
