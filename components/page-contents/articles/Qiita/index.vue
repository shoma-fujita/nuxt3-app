<template>
  <div class="qiita-articles">
    <article class="qiita-articles__item-list">
      <template v-for="article in data" :key="article.id">
        <div class="qiita-articles__item item">
          <a class="item__link" :href="article.url" />
          <div class="item__contents">
            <div class="item__header">
              <NuxtImg class="header__image" :src="article.user.profile_image_url" />
              <div class="header__information-area">
                <p class="header__author-name">{{ article.user.id }}</p>
                <p class="header__post-date">{{ article.created_at.substr(0, 10) }}</p>
              </div>
            </div>
            <h2 class="item__title">
              <a :href="article.url" class="item__title-link">{{ article.title }}</a>
            </h2>
          </div>
        </div>
      </template>
    </article>
    <hr>
  </div>
</template>

<script setup>
import { pageApiStore } from '@/store/page/qiita-articles/apiStore'

/** Page API Store */
const apiStore = pageApiStore()
apiStore.fetchArticles()

/** Qiita 記事一覧データ */
const data = apiStore.articles
</script>

<style lang="scss" scoped>
  @use './style.scss'
</style>