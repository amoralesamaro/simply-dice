<template>
  <ion-page>
    <ion-content :fullscreen="true" class="dice-content" @click="rollDice">
      <div class="dice-container">
        <div class="die" :class="{ rolling: isRolling }">
          <div class="pip" v-for="pip in getPips(die1)" :key="pip" :class="pip"></div>
        </div>
        
        <div class="die" :class="{ rolling: isRolling }">
          <div class="pip" v-for="pip in getPips(die2)" :key="pip" :class="pip"></div>
        </div>
      </div>
      
      <div class="instructions">Tap anywhere to roll</div>
    </ion-content>
  </ion-page>
</template>

<script setup lang="ts">
import { IonContent, IonPage } from '@ionic/vue';
import { ref } from 'vue';

const die1 = ref(1);
const die2 = ref(2); // Start with different numbers for visual interest
const isRolling = ref(false);

const rollDice = () => {
  if (isRolling.value) return;

  isRolling.value = true;

  // Wait for animation to finish before updating values
  setTimeout(() => {
    die1.value = Math.floor(Math.random() * 6) + 1;
    die2.value = Math.floor(Math.random() * 6) + 1;
    isRolling.value = false;
  }, 600); // Matches animation duration
};

// Returns an array of class names for pips based on the die value
const getPips = (value: number) => {
  const pipMap: Record<number, string[]> = {
    1: ['center'],
    2: ['top-left', 'bottom-right'],
    3: ['top-left', 'center', 'bottom-right'],
    4: ['top-left', 'top-right', 'bottom-left', 'bottom-right'],
    5: ['top-left', 'top-right', 'center', 'bottom-left', 'bottom-right'],
    6: ['top-left', 'top-right', 'middle-left', 'middle-right', 'bottom-left', 'bottom-right'],
  };
  return pipMap[value] || [];
};
</script>

<style scoped>
/* Main Layout */
.dice-content {
  --background: #000; /* Dark background as requested */
  --color: #fff;
  display: flex;
  justify-content: center;
  align-items: center;
  height: 100%;
}

.dice-container {
  display: flex;
  flex-direction: column;
  align-items: center;
  justify-content: center;
  gap: 60px; /* Space between dice */
  height: 100%;
  width: 100%;
}

.instructions {
  position: absolute;
  bottom: 40px;
  width: 100%;
  text-align: center;
  color: #666;
  font-size: 14px;
  pointer-events: none;
}

/* Die Styling */
.die {
  width: 100px;
  height: 100px;
  background: white; /* Fallback */
  background: radial-gradient(circle at 30% 30%, #ffffff, #e0e0e0);
  border-radius: 16px;
  box-shadow: 
    0 10px 20px rgba(0,0,0,0.5),
    inset 0 0 10px rgba(255,255,255,0.8),
    inset 0 -5px 15px rgba(0,0,0,0.1);
  position: relative;
  transition: transform 0.1s;
}

/* Pips Positioning */
.pip {
  width: 20px;
  height: 20px;
  background: #111;
  border-radius: 50%;
  position: absolute;
  box-shadow: inset 0 2px 3px rgba(0,0,0,0.6);
}

/* Grid system: 100x100 die. Pips are 20x20. */
/* Padding approx 10px from edges */

.center {
  top: 40px;
  left: 40px;
}

.top-left {
  top: 12px;
  left: 12px;
}

.top-right {
  top: 12px;
  right: 12px;
}

.bottom-left {
  bottom: 12px;
  left: 12px;
}

.bottom-right {
  bottom: 12px;
  right: 12px;
}

.middle-left {
  top: 40px;
  left: 12px;
}

.middle-right {
  top: 40px;
  right: 12px;
}

/* Rolling Animation */
.rolling {
  animation: roll 0.6s ease-in-out;
}

@keyframes roll {
  0% { transform: scale(1) rotate(0deg); }
  25% { transform: scale(0.9) rotate(90deg); }
  50% { transform: scale(1.1) rotate(180deg); }
  75% { transform: scale(0.9) rotate(270deg); }
  100% { transform: scale(1) rotate(360deg); }
}
</style>
