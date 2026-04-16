<template>
  <section id="core-value" class="core-value-section">
    <div class="grey-block-bg">
      <div class="core-value-content-container">
        <h2 class="section-title with-vertical-strip-orange">{{ $t('brand.brandStoryTitle') }}</h2>

        <h1 class="section-second-title">
          {{ $t('brand.intextLogo') }}
        </h1>

        <div class="text-container section-text text-color-dark-grey">
          <p class="story-paragraph fade-in" v-html="$t('brand.paragraph1')"></p>
          <p class="story-paragraph fade-in" v-html="$t('brand.paragraph2')"></p>
        </div>
      </div>
      <div class="core-value-section-bg-container">
        <img
          class="core-value-section-bg"
          src="/images/kitchen-interior.jpeg"
          alt="Modern smart home interior"
        />
      </div>
    </div>

    <!-- Founder Story Section -->
    <div class="founder-section">
      <div class="founder-content">
        <p class="story-paragraph fade-in" v-html="$t('brand.paragraph3')"></p>
        <p class="story-paragraph fade-in" v-html="$t('brand.paragraph4')"></p>
      </div>
    </div>

    <!-- Closing Statement -->
    <div class="closing-section">
      <div class="closing-content">
        <p class="closing-text fade-in" v-html="$t('brand.paragraph5')"></p>
      </div>
    </div>
  </section>
</template>

<script lang="ts">
import { defineComponent, onMounted } from 'vue'
import { useI18n } from 'vue-i18n'

export default defineComponent({
  name: 'CoreValue',
  setup() {
    const { locale } = useI18n()

    onMounted(() => {
      // Intersection Observer for fade-in animations
      const observer = new IntersectionObserver((entries) => {
        entries.forEach(entry => {
          if (entry.isIntersecting) {
            entry.target.classList.add('visible')
          }
        })
      }, { threshold: 0.15 })

      document.querySelectorAll('.fade-in').forEach(el => observer.observe(el))
    })

    return {
      locale
    }
  }
})
</script>

<style scoped lang="scss">
.core-value-section {
  height: auto !important;
  overflow: visible !important;
}

.fade-in {
  opacity: 0;
  transform: translateY(24px);
  transition: opacity 0.7s ease, transform 0.7s ease;
}

.fade-in.visible {
  opacity: 1;
  transform: translateY(0);
}

.story-paragraph {
  font-size: 1.08rem;
  line-height: 2;
  color: #444;
  margin-bottom: 28px;

  :deep(font[color="e05a35"]) {
    color: #e05a35;
    font-weight: 600;
  }

  // Legacy color code support
  :deep(font[color="c46043"]) {
    color: #e05a35;
    font-weight: 600;
  }
}

.section-second-title {
  font-size: 1.6rem;
  color: #e05a35;
  font-weight: 700;
  margin-bottom: 32px;
  line-height: 1.4;

  @media (max-width: 768px) {
    font-size: 1.25rem;
  }
}

.founder-section {
  background: #fff;
  padding: 60px 40px;
  position: relative;
  z-index: 1;

  @media (max-width: 768px) {
    padding: 40px 20px;
  }

  .founder-content {
    position: relative;
    max-width: 900px;
    margin: 0 auto;
    padding-left: 28px;
    border-left: 3px solid #e05a35;

    @media (max-width: 768px) {
      padding-left: 20px;
    }
  }
}

.closing-section {
  background: linear-gradient(135deg, #fff8f5, #fef3ee);
  padding: 60px 40px;
  text-align: center;
  position: relative;
  z-index: 1;

  @media (max-width: 768px) {
    padding: 40px 20px;
  }

  .closing-content {
    max-width: 750px;
    margin: 0 auto;
  }

  .closing-text {
    font-size: 1.2rem;
    line-height: 2;
    color: #333;
    font-weight: 500;

    :deep(font[color="e05a35"]),
    :deep(font[color="c46043"]) {
      color: #e05a35;
      font-weight: 700;
      font-size: 1.3rem;
    }

    @media (max-width: 768px) {
      font-size: 1.05rem;

      :deep(font[color="e05a35"]),
      :deep(font[color="c46043"]) {
        font-size: 1.1rem;
      }
    }
  }
}
</style>
