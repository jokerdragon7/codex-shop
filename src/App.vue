<script setup>
import { ref } from 'vue'

const menuOpen = ref(false)

const navigation = [
  { label: '首页', href: '#home' },
  { label: '菜单', href: '#menu' },
  { label: '关于我们', href: '#story' },
  { label: '联系我们', href: '#contact' },
]

const dishes = [
  { id: '01', name: '山野菌菇慢炖鸡', detail: '时令山珍 · 文火慢炖', image: 'image-one', featured: true },
  { id: '02', name: '脆皮北京烤鸭', detail: '枣木烤制 · 手工荷叶饼', image: 'image-two' },
  { id: '03', name: '清蒸东海黄鱼', detail: '当日鲜捕 · 金尊葱油', image: 'image-three' },
]

function closeMenu() {
  menuOpen.value = false
}
</script>

<template>
  <header class="header">
    <a class="brand" href="#home" aria-label="食遇首页"><span>食</span>遇<small>SHI YU</small></a>
    <button class="menu-toggle" aria-label="打开导航" :aria-expanded="menuOpen" @click="menuOpen = !menuOpen"><i></i><i></i></button>
    <nav class="nav" :class="{ open: menuOpen }" aria-label="主导航">
      <a v-for="(item, index) in navigation" :key="item.href" :class="{ active: index === 0 }" :href="item.href" @click="closeMenu">{{ item.label }}</a>
    </nav>
    <a class="reserve reserve-top" href="#reservation">立即预订 <b>↗</b></a>
  </header>

  <main id="home">
    <section class="hero">
      <div class="hero-content">
        <p class="eyebrow">MODERN CHINESE CUISINE</p>
        <h1>一席风味<br><em>恰逢其时</em></h1>
        <p class="intro">以时令入馔，以匠心传味。<br>在传统与新意之间，遇见东方餐桌的当代诗意。</p>
        <a class="reserve reserve-hero" href="#reservation">预订餐位 <b>↗</b></a>
      </div>
      <div class="scroll">SCROLL TO DISCOVER <span></span></div>
      <aside class="hero-meta"><p>上海 · 静安</p><p>11:30 — 22:30</p></aside>
    </section>

    <section id="menu" class="highlights">
      <p class="eyebrow">SEASONAL SELECTION</p>
      <div class="section-title"><h2>此刻，正当味</h2><a href="#menu">浏览完整菜单 <b>↗</b></a></div>
      <div class="dish-grid">
        <article v-for="dish in dishes" :key="dish.id" class="dish" :class="{ 'dish-large': dish.featured }">
          <div class="dish-image" :class="dish.image"></div>
          <div class="dish-info"><span>{{ dish.id }}</span><h3>{{ dish.name }}</h3><p>{{ dish.detail }}</p></div>
        </article>
      </div>
    </section>

    <section id="story" class="story">
      <div class="story-picture"></div>
      <div class="story-copy"><p class="eyebrow">OUR PHILOSOPHY</p><h2>让每一次相聚，<br>都有温度可循。</h2><p>食遇相信，好的食物不止于味觉。我们走访山川湖海，寻觅最诚实的食材；也在一方灶台前，耐心守候每一道风味的发生。</p><a href="#contact" class="text-link">了解食遇 <b>↗</b></a></div>
    </section>

    <section id="reservation" class="reservation-panel"><p class="eyebrow">A TABLE AWAITS</p><h2>留一席，等你来。</h2><a class="reserve" href="tel:021-88886666">电话预订 021 8888 6666 <b>↗</b></a></section>
  </main>

  <footer id="contact"><a class="brand" href="#home"><span>食</span>遇<small>SHI YU</small></a><p>上海市静安区愚园路 88 号 · 每日 11:30 — 22:30</p><p>© 2026 SHI YU RESTAURANT</p></footer>
</template>
