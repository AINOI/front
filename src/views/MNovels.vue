<template lang="pug">
b-container#MNovels(fluid)
  b-row.mt-5
    b-col.bg-white.rounded(cols='9')
      b-navbar.d-flex.justify-content-center
        b-navbar-nav.h5.w-100.d-flex.justify-content-around
          b-nav-item.aino-novel-rounded 測試標籤
          b-nav-item.aino-novel-rounded 測試標籤
          b-nav-item.aino-novel-rounded 測試標籤
          b-nav-item.aino-novel-rounded 測試標籤
          b-nav-item.aino-novel-rounded 測試標籤
          b-nav-item.aino-novel-rounded 測試標籤
          b-nav-item.aino-novel-rounded 測試標籤
          b-nav-item.aino-novel-rounded 測試標籤
    b-col.d-flex.align-items-center(cols='3')
      b-form.w-100
        b-form-group.w-100.mb-0
          //- b-input.aino-search-rounded(type='text' placeholder="文作查詢" @keydown.enter='search')
          b-input.mr-2.aino-search-rounded(type='text' placeholder="文作查詢")
          b-button(pill)
            b-icon-search

  b-row.my-0
    b-col.p-0(cols='9')
      b-container#novelslist(fluid)
        b-row
          b-col.mt-3(cols='12')
            .w-25.h-100.m-0.h1.type.aino-bg-wood
              | 恐怖
          b-col.d-flex.justify-content-end(cols='12')
            .overflow-auto
              b-pagination(:per-page='perPage' :total-rows='rows' v-model="currentPage")
          b-col(cols='12')
            b-table(:items="items" :per-page="perPage" :current-page="currentPage")
    b-col(cols='3')
      #createrlist
        b-navbar.novels-nav-border
          b-navbar-nav.w-100.d-flex.justify-content-around
            b-nav-item.aino-bg-third(@click='Ccreater') 推薦作者
            b-nav-item.aino-bg-third(@click='Cnovelslist') 推薦文作
          //- 作者列表
        b-row(v-if='creater')
          b-col(cols='4')
            img.rounded.w-100.h-50(src='https://picsum.photos/500/500/?random=10')
          b-col(cols='8')
            b-btn.w-100.h-50.border-0
              div Yamas*
        b-row(v-if='novelslist')
          b-col(cols='4')
            img.rounded.w-100.h-50(src='https://picsum.photos/500/500/?random=20')
          b-col(cols='8')
            b-btn.w-100.h-50.border-0
              div 華清的酒
</template>

<script>
export default {
  data () {
    return {
      creater: true,
      novelslist: false,
      perPage: 3,
      currentPage: 1,
      items: [
        { id: 1, first_name: 'Fred', last_name: 'Flintstone' },
        { id: 2, first_name: 'Wilma', last_name: 'Flintstone' },
        { id: 3, first_name: 'Barney', last_name: 'Rubble' },
        { id: 4, first_name: 'Betty', last_name: 'Rubble' },
        { id: 5, first_name: 'Pebbles', last_name: 'Flintstone' },
        { id: 6, first_name: 'Bamm Bamm', last_name: 'Rubble' },
        { id: 7, first_name: 'The Great', last_name: 'Gazzoo' },
        { id: 8, first_name: 'Rockhead', last_name: 'Slate' },
        { id: 9, first_name: 'Pearl', last_name: 'Slaghoople' }
      ]
    }
  },
  methods: {
    Ccreater () {
      if (this.creater === false) {
        this.creater = true
        this.novelslist = false
      }
    },
    Cnovelslist () {
      if (this.novelslist === false) {
        this.creater = false
        this.novelslist = true
      }
    }
  },
  computed: {
    rows () {
      return this.items.length
    }
  }
}
</script>

<style lang="scss">
@import '../../scss/aino-style.scss' ;

</style>
