<template>
  <div>
    <a-trigger trigger="hover" position="bl">
      <template #content>
        <sketch-picker :value="themeColor" @input="handleColorChange" />
      </template>

      <div :class="$style.input">
        <div :class="$style.color" :style="{ backgroundColor: themeColor }" />
        <span>{{ themeColor }}</span>
      </div>
    </a-trigger>

    <ul :class="$style.ul">
      <li
        v-for="(item, index) in colorList"
        :key="index"
        :class="$style.li"
        :style="{ backgroundColor: item }"
      />
    </ul>

    <a-typography-paragraph :style="{ fontSize: '12px' }">
      {{ $t('settings.color.tooltip') }}
    </a-typography-paragraph>
  </div>
</template>

<script setup lang="ts">
  import { ref, computed, onMounted } from 'vue';
  import { Trigger as ATrigger } from '@arco-design/web-vue';
  import { SketchPicker } from 'vue-color';
  import { generate, getRgbStr } from '@arco-design/color';
  import { useAppStore } from '@/store';

  // 获取主题
  const getTheme = () => {
    return (
      document.querySelector('body')?.getAttribute('arco-theme') || 'light'
    );
  };

  // 响应式数据
  const theme = ref(getTheme());
  const appStore = useAppStore();

  // 计算属性
  const themeColor = computed(() => appStore.themeColor);
  const colorList = computed(() => generate(themeColor.value, { list: true }));

  // 方法
  const handleColorChange = (color: any) => {
    // const newColor = color.hex;
    const newColor = color;

    appStore.updateSettings({
      themeColor: newColor,
    });

    // 生成新的颜色列表并更新 CSS 变量
    const newList = generate(newColor, {
      list: true,
      dark: theme.value === 'dark',
    });

    newList.forEach((l: any, index: number) => {
      const rgbStr = getRgbStr(l);
      document.body.style.setProperty(`--arcoblue-${index + 1}`, rgbStr);
    });
  };

  // 监听主题变化（如果需要）
  onMounted(() => {
    if (
      appStore.globalSettings &&
      !['#165DFF', '#165dff'].includes(appStore.themeColor)
    ) {
      handleColorChange(appStore.themeColor);
    }
  });
</script>

<style module lang="less">
  .input {
    display: flex;
    width: 100%;
    height: 32px;
    border: 1px solid var(--color-border);
    padding: 3px;
    box-sizing: border-box;
  }

  .color {
    width: 100px;
    height: 24px;
    margin-right: 10px;
  }

  .ul {
    list-style: none;
    display: flex;
    padding: 0;
  }

  .li {
    width: 10%;
    height: 26px;
  }
</style>
