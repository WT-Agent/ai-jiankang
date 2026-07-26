<template>
  <section class="nomads-showcase-section">
    <div class="showcase-header">
      <div class="header-left">
        <h2 class="showcase-title">实战案例与养生预设模板库 (Nomads Showcase)</h2>
        <p class="showcase-subtitle">精选科学养生与健康照护场景，点击“一键套用”快速生成专属调理方案</p>
      </div>
      <span class="showcase-badge">已收录 {{ showcaseItems.length }} 个健康实战模板</span>
    </div>

    <div class="showcase-grid">
      <div 
        v-for="item in showcaseItems" 
        :key="item.id" 
        class="glass-card showcase-card"
      >
        <div class="card-header">
          <span class="scenario-tag">{{ item.tag }}</span>
          <span class="usage-count">{{ item.usageCount }} 次应用</span>
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

export interface ShowcaseItem {
  id: string;
  tag: string;
  title: string;
  prompt: string;
  healthType?: string;
  targetGroup?: string;
  healthFocus?: string;
  usageCount: string;
}

const emit = defineEmits<{
  (e: 'apply-template', payload: {
    prompt: string;
    healthType?: string;
    targetGroup?: string;
    healthFocus?: string;
  }): void;
}>();

const showcaseItems = computed<ShowcaseItem[]>(() => [
  {
    id: 'jiankang-1',
    tag: '职场久坐',
    title: '程序员久坐腰颈痛与肩颈放松调理',
    prompt: '长时间电脑前工作，伴有颈椎僵硬、腰酸背痛与眼干眼疲劳，需要制定系统性的办公室伸展复健与护眼调理方案。',
    healthType: '职场久坐亚健康与腰颈调理',
    targetGroup: '职场白领',
    healthFocus: '护眼明目',
    usageCount: '34.2k'
  },
  {
    id: 'jiankang-2',
    tag: '睡眠调理',
    title: '长期失眠多梦与焦虑安神食疗',
    prompt: '入睡困难、夜间易醒且常伴有工作压力造成的轻度焦虑，请求提供助眠作息调整指南与温和安神食疗炖汤配方。',
    healthType: '睡眠改善与焦虑情绪舒缓',
    targetGroup: '职场白领',
    healthFocus: '改善睡眠',
    usageCount: '41.8k'
  },
  {
    id: 'jiankang-3',
    tag: '科学减脂',
    title: '低糖低脂抗糖餐单与控糖饮食',
    prompt: '希望在维持良好精神状态的同时控制体脂与血糖升幅，需要一份为期一周的低GI科学膳食食谱及日常替换食材建议。',
    healthType: '科学膳食减脂与营养餐单',
    targetGroup: '健身爱好者',
    healthFocus: '消化肠道调理',
    usageCount: '29.5k'
  },
  {
    id: 'jiankang-4',
    tag: '慢病养生',
    title: '中老年高血压日常饮食提醒与养生',
    prompt: '60岁以上长辈血压偏高，需控制钠盐摄入并保持血管弹性，请出具低盐低脂降压饮食法则及适度散步锻炼禁忌。',
    healthType: '中老年日常养生与慢病预防',
    targetGroup: '中老年长辈',
    healthFocus: '提升免疫力',
    usageCount: '38.6k'
  },
  {
    id: 'jiankang-5',
    tag: '产后复健',
    title: '产后气血恢复与肠道调理方案',
    prompt: '产后恢复期体力虚弱、消化不良且伴有睡眠不足，需要科学温补膳食配比与产后低强度核心恢复运动指引。',
    healthType: '科学膳食减脂与营养餐单',
    targetGroup: '产后妈妈',
    healthFocus: '消化肠道调理',
    usageCount: '27.4k'
  },
  {
    id: 'jiankang-6',
    tag: '免疫提升',
    title: '肠道消化不良与益生菌膳食调理',
    prompt: '经常腹胀、便秘或消化不良，免疫力较为低下，请求制定调理肠道菌群的膳食纤维搭配与日常生活禁忌。',
    healthType: '职场久坐亚健康与腰颈调理',
    targetGroup: '职场白领',
    healthFocus: '提升免疫力',
    usageCount: '31.1k'
  }
]);

function applyTemplate(item: ShowcaseItem) {
  emit('apply-template', {
    prompt: item.prompt,
    healthType: item.healthType,
    targetGroup: item.targetGroup,
    healthFocus: item.healthFocus
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
