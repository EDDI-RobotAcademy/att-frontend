<template>
  <div id="app">
    <!-- 기존 컴포넌트 -->
    <ExistingComponent />
    
    <!-- UnityComponent 추가 -->
    <UnityComponent />
  </div>
</template>

<script>
import ExistingComponent from './components/ExistingComponent.vue';
import UnityComponent from './components/UnityComponent.vue';

export default {
  name: 'App',
  components: {
    ExistingComponent,
    UnityComponent
  }
};
</script>

<style>
/* Global styles here */
</style>

<!-- <template>
  <v-app>
    <navigation-menu-bar/>
    <v-main>
      <router-view/>
    </v-main>
  </v-app>
</template>

<script lang="ts">
import { defineComponent } from 'vue'
import NavigationMenuBar from './navigationBar/NavigationMenuBar.vue';

export default defineComponent({
  
  components: { NavigationMenuBar },
  name: 'App',

  data () {
    return {
      //
    }
  },
})
</script>
 -->
