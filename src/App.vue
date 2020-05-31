<template lang="pug">
  v-app
    DraggableCard
</template>

<script>
import DraggableCard from './components/DraggableCard';

export default {
  name: 'App',

  components: {
    DraggableCard,
  },

  data: () => ({
    //
  }),
};
</script>
