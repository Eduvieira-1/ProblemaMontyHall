<template>
  <div class="door-area">
    <div class="door-frame" :class="{ selected: selected && !open }">
      <Gift v-if="open && hasGift" />
    </div>
    <div class="door" :class="{ open }" @click="selected = !selected">
      <div class="number" :class="{ selected }">{{ number }}</div>
      <div class="knob" :class="{ selected }" @click.stop="open = true"></div>
    </div>
  </div>
</template>

<script>
import Gift from "./Gift.vue";
export default {
  components: { Gift },
  props: {
    number: {},
    hasGift: { type: Boolean },
  },
  data() {
    return {
      open: false,
      selected: false,
    };
  },
};
</script>

<style>
:root {
  --door-border: 5px solid brown;
  --selected-border: 5px solid yellow;
}

.door-area {
  position: relative;
  width: 200px;
  height: 300px;
  border-bottom: 10px solid #aaa;
  margin-bottom: 25px;
  font-size: 3rem;
  display: flex;
  justify-content: center;
}

.door-frame {
  display: flex;
  justify-content: center;
  align-items: flex-end;
  position: absolute;
  width: 180px;
  height: 290px;
  border-right: var(--door-border);
  border-top: var(--door-border);
  border-left: var(--door-border);
}

.door {
  position: absolute;
  top: 5px;
  width: 170px;
  height: 285px;
  background-color: chocolate;
  display: flex;
  flex-direction: column;
  align-items: center;
}

.door .knob {
  height: 20px;
  width: 20px;
  border-radius: 10px;
  background-color: brown;
  align-self: flex-start;
  margin-left: 20px;
  margin-top: 95px;
}

/* Quando selecionado */
.door-frame.selected {
  border-right: var(--selected-border);
  border-top: var(--selected-border);
  border-left: var(--selected-border);
}

.door > .number.selected {
  color: yellow;
}

.door > .knob.selected {
  background-color: yellow;
}

.door.open {
  background-color: #0007;
}

.door.open .knob {
  display: none;
}

.door.open .number {
  display: none;
}
</style>