<template>
  <div class="glass-card ticker-card">
    <div class="ticker-wrapper">
      <div v-for="(item, index) in tickerItems" :key="index" class="ticker-item">
        <span>{{ item.text }}</span>
        <span style="color: var(--success-color); font-weight: bold;">[测试分析完成]</span>
      </div>
    </div>
  </div>
</template>

<script setup lang="ts">
import { ref } from 'vue';

const tickerItems = ref([
  { text: '用户 136****4912 完成了 INFP 调停者深层心理特质与能量恢复解析' },
  { text: '用户 178****8209 完成了高情商社交沟通与恋爱相处模式测试' },
  { text: '用户 181****0193 完成了 ENTJ 指挥官职场领导力潜能评估' },
  { text: '用户 133****5520 解锁了趣味猫咪型性格图腾与社交护城河' },
  { text: '用户 159****9918 完成了职场内耗与心理防御机制自测方案' },
]);
</script>
