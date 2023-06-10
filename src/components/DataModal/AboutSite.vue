<template>
  <!-- 关于本站 -->
  <n-modal
    class="s-modal"
    v-model:show="showAboutModal"
    preset="card"
    :title="$t('nav.avatar.about')"
    :bordered="false"
    transform-origin="center"
  >
    <div class="copyright">
      <div class="desc">
        <n-text class="name">{{ siteTitle }}</n-text>
        <n-text class="version" :depth="3">
          v&nbsp;{{ packageJson.version }}
        </n-text>
      </div>
      <n-blockquote>
        <n-text class="power">
          Copyright&nbsp;©&nbsp;2019 - {{ new Date().getFullYear() }}
        </n-text>
      </n-blockquote>
    </div>
  </n-modal>
</template>

<script setup>
import packageJson from "@/../package.json";

// 关于本站数据
const siteTitle = import.meta.env.VITE_SITE_TITLE;
const showAboutModal = ref(false);
const icp = ref(import.meta.env.VITE_ICP ? import.meta.env.VITE_ICP : null);

// 链接跳转
const jumpUrl = (url) => {
  window.open(url);
};

// 开启本站数据弹窗
const openAboutSite = () => {
  showAboutModal.value = true;
};

// 暴露方法
defineExpose({
  openAboutSite,
});
</script>

<style lang="scss" scoped>
.copyright {
  display: flex;
  flex-direction: column;
  a {
    text-decoration: none;
  }
  .name {
    font-size: 30px;
    font-weight: bold;
  }
  .version {
    margin-left: 6px;
  }
  .n-blockquote {
    @media (max-width: 768px) {
      display: flex;
      flex-direction: column;
      .point {
        display: none;
      }
    }
    .point {
      margin: 0 4px;
    }
  }
  .github {
    margin-top: 8px;
  }
}
</style>
