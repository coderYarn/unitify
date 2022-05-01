<template>
  <view class="swiper">
    <Pages>
      <Block title="基础使用">
        <CheckBox checked> 复选框 </CheckBox>
      </Block>
      <Block title="禁用状态">
        <CheckBox v-model="checkedVal" checked disabled> 复选框 </CheckBox>
        <CheckBox v-model="checkedVal" disabled> 复选框 </CheckBox>
      </Block>
      <Block title="自定义形状">
        <CheckBox v-model="checkedVal" shape="square" checked>
          复选框
        </CheckBox>
      </Block>
      <Block title="自定义形状">
        <CheckBox v-model="checkedVal" color="rgb(238, 10, 36)" checked>
          复选框
        </CheckBox>
      </Block>
      <Block title="自定义大小">
        <CheckBox v-model="checkedVal" size="48rpx" checked> 复选框 </CheckBox>
      </Block>
      <Block title="禁用文本点击">
        <CheckBox v-model="checkedVal" label-disabled checked> 复选框 </CheckBox>
      </Block>
    </Pages>
  </view>
</template>

<script lang="ts">
import { defineComponent, ref } from "vue";
import Pages from "@/components/pages/pages.vue";
import Block from "@/components/block/block.vue";

export default defineComponent({
  components: { Pages, Block },
  setup() {
    const checkedVal = ref(false);
    const handleClick = () => {
      console.log(checkedVal.value);
    };
    return {
      handleClick,
      checkedVal,
    };
  },
});
</script>
<style lang="scss" scoped>
.block {
  width: 100%;

  padding: 0;
}
</style>
