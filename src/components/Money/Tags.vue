<template>
  <div class="tags">
    <span v-for="tag in currentTags" :key="tag">
      <Icon :name="tag" class="icons"></Icon>
      {{ tag }}
    </span>
  </div>
</template>

<script lang='ts'>
import Vue from "vue";
import { Component } from "vue-property-decorator";

@Component
export default class Tags extends Vue {
  get type() {
    return this.$store.state.type;
  }
  get currentTags() {
    if (this.type === "-") {
      return this.$store.state.payTags;
    } else {
      return this.$store.state.incomeTags;
    }
  }
}
</script>

<style lang='scss' scoped>
.icons {
  color: darken(#ffda8e, 10%);
}
.tags {
  display: flex;
  font-size: 10px;
  padding: 16px;
  flex-wrap: wrap;
  align-content: flex-start;
  background: #fff;
  flex-grow: 1;
  .icon {
    width: 24px;
    height: 24px;
  }

  span {
    display: flex;
    flex-direction: column;

    margin: 10px 20px;
  }
}
</style>