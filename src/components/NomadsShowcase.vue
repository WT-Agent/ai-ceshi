<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">趣味性格与心理测试实战模板库</h2>
        <p class="showcase-subtitle">精选 MBTI 画像、恋爱情商与职场潜能测评，点击“一键套用”生成心理解析</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个测试分析模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次测评</span>
        </div>

        <div class="card-content">
          <h3 class="item-title">{{ item.title }}</h3>
          <p class="item-prompt">“{{ item.prompt }}”</p>
        </div>

        <div class="card-action">
          <button class="apply-btn" @click="applyTemplate(item)">
            <span>一键套用</span>
            <svg class="arrow-icon" viewBox="0 0 24 24" fill="none" stroke="currentColor" stroke-width="2">
              <line x1="5" y1="12" x2="19" y2="12"></line>
              <polyline points="12 5 19 12 12 19"></polyline>
            </svg>
          </button>
        </div>
      </div>
    </div>
  </section>
</template>

<script setup lang="ts">
import { computed } from 'vue';

const emit = defineEmits<{
  (e: 'apply-template', payload: { prompt: string; testType?: string; dimension?: string }): void;
}>();

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  testType?: string;
  dimension?: string;
  usageCount: string;
}

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'ceshi-1',
    tag: 'MBTI画像',
    title: 'INFP 调停者深度心灵画像与能量恢复',
    prompt: '为 INFP 精神内耗与高敏感人群生成一份心理画像，剖析其深层理想主义、直觉共情力及社交充电指南。',
    testType: 'MBTI与性格基因深度画像',
    dimension: '认知思维与决策偏好',
    usageCount: '69.4k'
  },
  {
    id: 'ceshi-2',
    tag: '职场潜能',
    title: 'ENTJ 指挥官型职场天花板突破测评',
    prompt: '分析 ENTJ 高执行力与果断决策特质在职场晋升中的优势，并警示可能存在的过于强势与忽视下属情绪盲点。',
    testType: '职场潜能与领导力风格',
    dimension: '职场天赋与潜能开发',
    usageCount: '53.1k'
  },
  {
    id: 'ceshi-3',
    tag: '恋爱情商',
    title: '回避型依恋与焦虑型依恋沟通破局',
    prompt: '测试恋爱关系中当一方回避另一方焦虑时的心理互动模式，提供建立安全型依恋与非暴力沟通的破局方案。',
    testType: '恋爱相处与情商社交',
    dimension: '人际沟通与情商社交',
    usageCount: '61.8k'
  },
  {
    id: 'ceshi-4',
    tag: '趣味拟人',
    title: '独立高冷猫咪型性格图腾与社交边界',
    prompt: '将“表面高冷、内心温暖、注重独立空间”的人格比作猫咪图腾，生成一份趣味动物性格诊断与社交边界声明。',
    testType: '趣味角色原型与动物性格',
    dimension: '人际沟通与情商社交',
    usageCount: '47.2k'
  },
  {
    id: 'ceshi-5',
    tag: '讨好心理',
    title: '讨好型人格与拒绝恐惧心理防御机制',
    prompt: '剖析习惯性迎合他人、不敢表达拒绝的深层讨好型心理，提供建立心理防线与提升自我认同感练习。',
    testType: 'MBTI与性格基因深度画像',
    dimension: '情绪压力与自我防卫',
    usageCount: '44.9k'
  },
  {
    id: 'ceshi-6',
    tag: '情绪诊断',
    title: '职场电量耗尽与心理倦怠状态自测',
    prompt: '针对长工作时间带来的心理疲惫感，自测当前心理电量百分比，提供物理隔离与精神断舍离治愈建议。',
    testType: '职场潜能与领导力风格',
    dimension: '情绪压力与自我防卫',
    usageCount: '58.3k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    testType: item.testType,
    dimension: item.dimension
  });
}
</script>

<style scoped>
.nomads-showcase-section {
  margin-top: 2rem;
  width: 100%;
}

.showcase-header {
  display: flex;
  justify-content: space-between;
  align-items: flex-end;
  margin-bottom: 1.25rem;
  padding-bottom: 0.75rem;
  border-bottom: 1px solid var(--card-border);
}

.showcase-title {
  font-size: 1.2rem;
  font-weight: 700;
  color: var(--text-primary);
  background: var(--primary-gradient);
  -webkit-background-clip: text;
  -webkit-text-fill-color: transparent;
}

.showcase-subtitle {
  font-size: 0.825rem;
  color: var(--text-secondary);
  margin-top: 0.25rem;
}

.showcase-badge {
  font-size: 0.75rem;
  color: #a5b4fc;
  background: rgba(99, 102, 241, 0.12);
  border: 1px solid rgba(99, 102, 241, 0.25);
  padding: 4px 10px;
  border-radius: 20px;
}

.showcase-grid {
  display: grid;
  grid-template-columns: repeat(1, 1fr);
  gap: 1.25rem;
}

@media (min-width: 640px) {
  .showcase-grid {
    grid-template-columns: repeat(2, 1fr);
  }
}

@media (min-width: 1024px) {
  .showcase-grid {
    grid-template-columns: repeat(3, 1fr);
  }
}

.showcase-card {
  display: flex;
  flex-direction: column;
  justify-content: space-between;
  height: 100%;
  padding: 1.25rem;
  background: rgba(255, 255, 255, 0.02);
  border: 1px solid var(--card-border);
  border-radius: 14px;
  transition: all 0.25s ease;
}

.showcase-card:hover {
  background: rgba(255, 255, 255, 0.05);
  border-color: rgba(99, 102, 241, 0.4);
  transform: translateY(-3px);
  box-shadow: 0 10px 25px rgba(0, 0, 0, 0.4);
}

.card-header {
  display: flex;
  justify-content: space-between;
  align-items: center;
  margin-bottom: 0.75rem;
}

.scenario-tag {
  font-size: 0.75rem;
  font-weight: 600;
  padding: 3px 8px;
  border-radius: 6px;
  background: rgba(168, 85, 247, 0.15);
  color: #c084fc;
  border: 1px solid rgba(168, 85, 247, 0.3);
}

.usage-count {
  font-size: 0.75rem;
  color: var(--text-secondary);
}

.card-content {
  margin-bottom: 1rem;
  flex: 1;
}

.item-title {
  font-size: 0.95rem;
  font-weight: 600;
  color: var(--text-primary);
  margin-bottom: 0.4rem;
}

.item-prompt {
  font-size: 0.825rem;
  color: var(--text-secondary);
  line-height: 1.45;
  display: -webkit-box;
  -webkit-line-clamp: 3;
  -webkit-box-orient: vertical;
  overflow: hidden;
  font-style: italic;
}

.card-action {
  padding-top: 0.75rem;
  border-top: 1px solid rgba(255, 255, 255, 0.04);
}

.apply-btn {
  width: 100%;
  display: flex;
  align-items: center;
  justify-content: center;
  gap: 6px;
  padding: 0.5rem 1rem;
  background: rgba(99, 102, 241, 0.1);
  border: 1px solid rgba(99, 102, 241, 0.3);
  border-radius: 8px;
  color: #a5b4fc;
  font-size: 0.825rem;
  font-weight: 600;
  cursor: pointer;
  transition: all 0.2s ease;
}

.showcase-card:hover .apply-btn {
  background: var(--primary-gradient);
  border-color: transparent;
  color: white;
}

.arrow-icon {
  width: 14px;
  height: 14px;
  transition: transform 0.2s ease;
}

.apply-btn:hover .arrow-icon {
  transform: translateX(3px);
}
</style>
