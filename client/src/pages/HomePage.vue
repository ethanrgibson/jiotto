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


document.addEventListener('DOMContentLoaded', function () {
      // Get all the necessary elements from the DOM
      const sliderContainer = document.querySelector('.slider-container');
      const prevBtn = document.getElementById('prevBtn');
      const nextBtn = document.getElementById('nextBtn');

      // Get all individual slide elements
      const slides = document.querySelectorAll('.cardContainer');
      const slideCount = slides.length;

      // Set the initial index to the first slide
      let currentIndex = 0;

      // Function to update the slider's position
      function updateSlider() {
        // Calculate the amount to move the container
        const offset = -currentIndex * 100;
        // Apply the transformation
        sliderContainer.style.transform = `translateX(${offset}%)`;

        // Update the state of the navigation buttons
        updateButtons();
      }

      // Function to enable or disable the prev/next buttons
      function updateButtons() {
        // Disable the 'prev' button if we are at the first slide
        if (currentIndex === 0) {
          prevBtn.disabled = true;
        } else {
          prevBtn.disabled = false;
        }

        // Disable the 'next' button if we are at the last slide
        if (currentIndex === slideCount - 1) {
          nextBtn.disabled = true;
        } else {
          nextBtn.disabled = false;
        }
      }

      // Event listener for the 'next' button
      nextBtn.addEventListener('click', () => {
        // Move to the next slide if we are not at the end
        if (currentIndex < slideCount - 1) {
          currentIndex++;
          updateSlider();
        }
      });

      // Event listener for the 'previous' button
      prevBtn.addEventListener('click', () => {
        // Move to the previous slide if we are not at the beginning
        if (currentIndex > 0) {
          currentIndex--;
          updateSlider();
        }
      });

      // Initialize the slider and buttons on page load
      updateSlider();
    });

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

  <div class="slider-wrapper">
    <div class="slider-viewport">
      <div class="slider-container">

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
                  1. Find the right place.
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
        <div class="cardContainer">
          <div class="cardBackground">
            <div class="cardContent">
              <div>
                <img class="numberIcon"
                  src="https://via.placeholder.com/42/FFC107/000000?Text=2" alt="Number 2">
              </div>
              <div>
                <b style="font-size: 32px;">
                  2. This is the second slide.
                </b>
              </div>
              <div>
                <p style="font-size: 20px;">
                  You can change the text and images for this slide to create your second card.
                </p>
              </div>
            </div>
            <div>
              <img src="https://via.placeholder.com/445x512/cccccc/000000?text=Card+Image+2" class="cardImage">
            </div>
          </div>
        </div>
        <div class="cardContainer">
          <div class="cardBackground">
            <div class="cardContent">
              <div>
                <img class="numberIcon"
                  src="https://via.placeholder.com/42/4CAF50/FFFFFF?Text=3" alt="Number 3">
              </div>
              <div>
                <b style="font-size: 32px;">
                  3. This is the third slide.
                </b>
              </div>
              <div>
                <p style="font-size: 20px;">
                  This is another card that you can customize with your own content.
                </p>
              </div>
            </div>
            <div>
              <img src="https://via.placeholder.com/445x512/9E9E9E/FFFFFF?text=Card+Image+3" class="cardImage">
            </div>
          </div>
        </div>
        <div class="cardContainer">
          <div class="cardBackground">
            <div class="cardContent">
              <div>
                <img class="numberIcon"
                  src="https://via.placeholder.com/42/2196F3/FFFFFF?Text=4" alt="Number 4">
              </div>
              <div>
                <b style="font-size: 32px;">
                  4. This is the fourth slide.
                </b>
              </div>
              <div>
                <p style="font-size: 20px;">
                  Keep adding your content to each of the cards as needed.
                </p>
              </div>
            </div>
            <div>
              <img src="https://via.placeholder.com/445x512/607D8B/FFFFFF?text=Card+Image+4" class="cardImage">
            </div>
          </div>
        </div>
        <div class="cardContainer">
          <div class="cardBackground">
            <div class="cardContent">
              <div>
                <img class="numberIcon"
                  src="https://via.placeholder.com/42/E91E63/FFFFFF?Text=5" alt="Number 5">
              </div>
              <div>
                <b style="font-size: 32px;">
                  5. This is the final slide.
                </b>
              </div>
              <div>
                <p style="font-size: 20px;">
                  This is the last card in the slider. The 'Next' button will be disabled.
                </p>
              </div>
            </div>
            <div>
              <img src="https://via.placeholder.com/445x512/795548/FFFFFF?text=Card+Image+5" class="cardImage">
            </div>
          </div>
        </div>
        </div>
    </div>

    <button id="prevBtn" class="slider-button">‹</button>
    <button id="nextBtn" class="slider-button">›</button>

  </div>

</template>

<style scoped lang="scss">
.slider-wrapper {
      position: relative;
      /* Width of a single card */
      width: 1083px;
      /* Center the slider */
      margin: auto;
    }

    .slider-viewport {
      /* This is the window that shows one card */
      overflow: hidden;
      width: 100%;
    }

    .slider-container {
      /* This container holds all cards in a row */
      display: flex;
      /* Animation for smooth sliding */
      transition: transform 0.5s ease-in-out;
    }

    .slider-button {
      position: absolute;
      top: 50%;
      transform: translateY(-50%);
      background-color: rgba(0, 0, 0, 0.6);
      color: white;
      border: none;
      font-size: 2rem;
      padding: 0.5rem 1rem;
      cursor: pointer;
      z-index: 10;
      border-radius: 8px;
    }

    .slider-button:hover {
      background-color: rgba(0, 0, 0, 0.9);
    }

    .slider-button:disabled {
      background-color: rgba(0, 0, 0, 0.2);
      cursor: not-allowed;
    }

    #prevBtn {
      left: 15px;
    }

    #nextBtn {
      right: 15px;
    }


    /* YOUR CARD STYLES (PROVIDED) */
    .cardContainer {
      /* Ensures each card stays rigid and doesn't shrink */
      flex-shrink: 0;
      width: 100%;
    }

    .cardBackground {
      display: flex;
      background-image: url(https://safeut.utahhealth.acsitefactory.com/sites/g/files/zrelqx271/files/media/images/2025/carousel.png);
      background-repeat: no-repeat;
      width: 1083px;
      height: 512px;
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
      width: 445.1px;
      height: 512px;
    }

@media screen AND (max-width: 576px) {
  .cardContainer {
    display: block;
  }

  .cardBackground {
    display: block;
  }

  .cardContent {
    display: block;
  }
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
