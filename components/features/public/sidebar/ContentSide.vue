<template>
  <div>
    <nav class="text-base capitalize">
      <div v-for="side in sideList" :key="side.id"> 
        <nuxt-link v-if="!side.list" :to="side.path" class="flex items-center nav">
          <div class="flex items-center">
            <i class="mr-4 text-h5 w-6" :class="side.icon"></i>
            {{side.name}}
          </div>
        </nuxt-link> 
        <!-- dropdown -->
        <div v-else class="flex items-center text-black text-body py-3 pl-6 hover:no-underline hover:text-primary-dark hover:bg-primary-light cursor-pointer" @click="side.open = !side.open">
          <div class="flex justify-between w-full items-center mr-3">
            <div class="flex items-center">
              <i class="mr-4 text-h5 w-6" :class="side.icon"></i>
              <p>{{side.name}}</p>
            </div>
            <i :class="side.open ? 'fas fa-angle-down' : 'fas fa-angle-right'"></i>
          </div>
        </div>
        <div v-for="lis in side.list" :key="lis.id" class="bg-white min-w-full">
          <div v-if="side.open" class="cursor-pointer">
            <nuxt-link :to="lis.path" class="ml-8 pl-6 border-l-2  py-3 block text-black text-body hover:no-underline hover:text-primary-dark hover:bg-primary-light">{{lis.name}}</nuxt-link>
          </div>
        </div>
      </div>
    </nav>
  </div>
</template>


<script lang="ts">
import Vue from 'vue'
export default Vue.extend({
  name: 'ContentSideBar',
  props: {
    sideList: { type: Array, default: () => [] } 
  },
  methods: {
    toPage(path: any) {
      this.$router.push(path)
    }
  }
})
</script>


<style lang="postcss" scoped>
.nav {
	@apply text-black text-body py-3 pl-6 hover:no-underline hover:text-primary-dark hover:bg-primary-light cursor-pointer;
}

a.nuxt-link-exact-active {
  @apply no-underline text-primary-dark bg-primary-light;
}
</style>