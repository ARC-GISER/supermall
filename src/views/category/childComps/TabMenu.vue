<template>
  <scroll id="tab-menu">
    <div class="menu-list">
      <div class="menu-list-item"
            v-for="(item,index) in categories"
           :key="index"
           :class="{active: index === currentIndex}"
           @click="itemClick(index)"
            >
            {{item.title}}
      </div>
    </div>
  </scroll>
</template>

<script>
  import Scroll from "../../components/common/scroll/Scroll";

  export default {
    name: "TabMenu",
    props: {
      categories:Array
    },
    components: {
      Scroll
    },
    data() {
      return {
        currentIndex:0
      }
    },
    methods: {
      itemClick(index) {
        this.currentIndex = index
        // 向父组件中传递一个选择item 的事件，并把当前的参数即当前item 的位置也传递给父组件
        this.$emit('selectItem',index)

      }
    }
  }
</script>

<style scoped>
    #tab-menu {
      background-color: #f6f6f6;
      height: 100%;
      width: 20%;
      box-sizing: border-box;
    }

    .menu-list-item {
      height: 45px;
      line-height: 45px;
      text-align: center;
      font-size: 14px;
    }

     .active {
      font-weight: 700;
      color: var(--color-high-text);
      background-color: #fff;
      border-left: 3px solid var(--color-high-text);
    }
</style>
