<template lang="pug">
  .card-wrapper(ref="draggable-card", :style="pos" @mousedown="startDrag")
    v-card
      v-card-text hello
</template>

<style scoped lang="scss">
  .card-wrapper {
    position:absolute
  }
</style>

<script>
export default {
  data() {
    return {
      curPosX: 0,
      curPosY: 0,
      moveDisX: 0,
      moveDisY: 0,
      draggCard: null,
      isDragging: false,
    }
  },
  mounted() {
    this.draggCard = this.$refs["draggable-card"]
    window.addEventListener("mouseup", this.stopDrag)
    window.addEventListener("mousemove", this.dragging)
  },
  computed: {
    pos() {
      if(this.draggCard) {
        return {
          left: (this.draggCard.offsetLeft - this.moveDisX) + "px",
          top: (this.draggCard.offsetTop - this.moveDisY) + "px"
        }
      }
      return {top: 0, left: 0}
    }
  },
  methods: {
    startDrag(e){
      this.isDragging = true
      this.curPosX = e.clientX
      this.curPosY = e.clientY
    },
    stopDrag(){
      this.isDragging = false
    },
    dragging(e){
      if (this.isDragging) {
        this.moveDisX = this.curPosX - e.clientX
        this.moveDisY = this.curPosY - e.clientY
        this.curPosX = e.clientX
        this.curPosY = e.clientY
      }
    }
  }
}
</script>