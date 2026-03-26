<script setup lang="ts">
import { watch, ref, nextTick } from 'vue';

const props = defineProps({
    state: {
        type: String,
        default: 'flying'
    }
});

const planeRef = ref<HTMLElement | null>(null);
const dynamicStyle = ref<Record<string, string>>({});

watch(() => props.state, async (newState, oldState) => {
  if (oldState === 'flying' && newState === 'landing' && planeRef.value) {
    const computed = window.getComputedStyle(planeRef.value);
    const currentTransform = computed.transform;
    const currentLeft = computed.left;
    const currentTop = computed.top;
    
    dynamicStyle.value = {
      transform: currentTransform,
      left: currentLeft,
      top: currentTop,
      transition: 'none',
      animation: 'none'
    };

    await nextTick();
    
    requestAnimationFrame(() => {
      requestAnimationFrame(() => {
        dynamicStyle.value = {};
      });
    });
  }
});
</script>

<template>
  <div 
    ref="planeRef" 
    class="plane-container" 
    :class="state"
    :style="dynamicStyle"
  >
    <div class="plane">
      <div class="wings"></div>
      
      <div class="engine left-engine"></div>
      <div class="engine right-engine"></div>
      
      <div class="tail"></div>
      
      <div class="fuselage"></div>
      
      <div class="cockpit"></div>
    </div>
  </div>
</template>

<style scoped>
.plane-container {
  position: absolute;
  top: 50%;
  left: 50%;
  margin-top: -40px; 
  margin-left: -40px;
  width: 80px;
  height: 80px;
  z-index: 10;
}

.plane-container.flying {
  animation: airplane-orbit 40s linear infinite;
}

.plane-container.flying .plane {
  transform: scale(1.6);
  filter: drop-shadow(-30px 35px 20px rgba(0, 0, 0, 0.2));
  transition: all 1.5s ease;
}

@keyframes airplane-orbit {
  0% { transform: rotate(0deg) translateY(-300px) rotate(90deg); }
  100% { transform: rotate(360deg) translateY(-300px) rotate(90deg); }
}

.plane-container.landing {
  left: 15%; 
  top: 50%;
  transform: rotate(90deg); 
  transition: all 4s ease-out; 
}

.plane-container.landing .plane {
  transform: scale(1.1);
  filter: drop-shadow(-8px 10px 8px rgba(0, 0, 0, 0.4));
  transition: all 4s ease-out;
}

.plane-container.taxiing {
  left: 80%;
  top: 50%;
  transform: rotate(90deg);
  transition: all 8s ease-in-out;
}

.plane-container.taxiing .plane {
  transform: scale(1);
  filter: drop-shadow(0px 3px 3px rgba(0, 0, 0, 0.6));
  transition: all 1.5s ease;
}

.plane {
  position: relative;
  width: 100%;
  height: 100%;
  display: flex;
  justify-content: center;
}

.fuselage {
  position: absolute;
  width: 22px;
  height: 76px;
  background: linear-gradient(to right, #e0e0e0, #ffffff, #e0e0e0);
  border-radius: 50% 50% 12% 12%;
  z-index: 3;
}

.cockpit {
  position: absolute;
  top: 12px;
  width: 14px;
  height: 16px;
  background-color: #0277bd;
  border-radius: 50% 50% 20% 20%;
  z-index: 4;
}

.wings {
  position: absolute;
  top: 30px;
  width: 80px;
  height: 20px;
  background-color: #f5f5f5;
  border-radius: 50% 50% 40% 40% / 30% 30% 70% 70%;
  z-index: 2;
}

.engine {
  position: absolute;
  top: 42px;
  width: 12px;
  height: 18px;
  background-color: #757575; 
  border-radius: 6px;
  z-index: 1;
}

.left-engine {
  left: 12px;
}

.right-engine {
  right: 12px;
}

.tail {
  position: absolute;
  bottom: 6px;
  width: 36px;
  height: 12px;
  background-color: #f5f5f5;
  border-radius: 12px 12px 6px 6px;
  z-index: 2;
}
</style>
