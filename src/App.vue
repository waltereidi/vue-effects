<script>
import { ref } from 'vue'
export default {
  data() {
    return {
      show: true,
      v1: false,
      v2: true,
    }
  },
  methods: {
    time() {

      setTimeout(async () => {
        if (this.v2) {
          setTimeout(async () => {

            this.v1 = !this.v1;
          }, 2000)
          this.v2 = !this.v2;

        } else {
          setTimeout(async () => {
            this.v2 = !this.v2;

          }, 2000)
          this.v1 = !this.v1;
        }
        this.time();

      }, 4000);
    }
  },
  mounted() {
    this.time();

  }
}


</script>
<template>
  <div class="grid">
    <div v-if="v1" class="grid-item1"></div>
    <div v-if="v2" class="grid-item2"></div>
    <div v-if="v1" class="grid-item3"></div>
    <div v-if="v1" class="grid-item1"></div>
    <div v-if="v2" class="grid-item2"></div>
    <div v-if="v2" class="grid-item3"></div>
    <div v-if="v1" class="grid-item1"></div>
    <div v-if="v2" class="grid-item2"></div>
    <div v-if="v1" class="grid-item3"></div>
  </div>
  <Transition>
    <img v-if="v1"
      src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcRQLqf99SQ-hla7CNrdfBW9c0TDxGRdIM8EhiSQRuoade3c2EdtP2Wt3VBDWiZMtfOMrPs&usqp=CAU">

  </Transition>
  <Transition>
    <img v-if="v2"
      src="https://encrypted-tbn0.gstatic.com/images?q=tbn:ANd9GcQ-libr-eczcsyfwHk_qcOymtJJKEii1zuChxG3OrB2LdTyxTIOCqRrmcUhsLuHAw83Bks&usqp=CAU" />
  </Transition>
  <br>
  <button @click="show = !show">Toggle</button>
  <Transition>
    <p v-if="show">hello</p>
  </Transition>
</template>
<style scoped>
@import "@/assets/main.scss";

.v-enter-active,
.v-leave-active {
  transition: opacity 0.3s ease;
}

.v-enter-from,
.v-leave-to {
  opacity: 0;
}
</style>