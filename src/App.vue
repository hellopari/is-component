<template>
<div id="dynamic-component-demo" class="demo">
    <button
        v-for="tab in tabs"
        :key="tab"
        :class="['tab-button', { active: currentTab === tab }]"
        @click="currentTab = tab"
    >
    {{ tab }}
    </button>
    <keep-alive>
        <component :is="currentTabComponent" class="tab"></component>
    </keep-alive>
    <base-input></base-input>
</div>
</template>

<script>
export default{
    data() {
      return {
        currentTab: 'Home',
        tabs: ['Home', 'Posts', 'Archive']
      }
    },
    computed: {
      currentTabComponent() {
        return 'tab-' + this.currentTab.toLowerCase()
      }
    }
}
</script>

<style>
#app {
  font-family: Avenir, Helvetica, Arial, sans-serif;
  -webkit-font-smoothing: antialiased;
  -moz-osx-font-smoothing: grayscale;
  text-align: center;
  color: #2c3e50;
  margin-top: 60px;
}
</style>
