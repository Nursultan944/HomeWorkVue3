<template>
  <div class="card">
    <h3>{{ title }}</h3>
    <app-button
      @action="open"
     >{{ isNewsOpen ? 'Закрыть': 'Открыть'}}
    </app-button>

    <app-button
      color="danger"

      v-if="wasRead"
      @action="$emit('unmark', id)">
      Отмеить непрочитанной
    </app-button>
    <div v-if="isNewsOpen">
      <hr />
       <p >Джо Байден набрал более 270 голосов выборщиков, необходимых для победы на президентских выборах, однако это не значит, что он уже завтра сможет переехать в Белый дом.</p>
      <app-button

        v-if="!wasRead"
        color="primary"
        @action="mark">
        Прочесть новость
      </app-button>

      <app-news-list >

      </app-news-list>

    </div>
  </div>
</template>

<script>
import AppButton from './AppButton'
import AppNewsList from './AppNewsList'
export default {
  name: 'AppNews',
  props: {

    wasRead: Boolean,
    title: {
      type: String,
      required: true
    },

    id: {
      type: Number,
      required: true
    },
    isOpen: {
      type: Boolean,
      required: false,
      default: false,
      validator (value) {
        return value === true || value === false
      }
    }
  },
  // emits: ['open-news'],
  emits: {
    'open-news': null,
    'read-news' (id) {
      if (id) {
        return true
      }
      console.warn('Нет параметра id для emit read-news')
      return false
    },
    unmark: null

  },
  data () {
    return {

      isNewsOpen: this.isOpen
    }
  },
  methods: {
    open () {
      this.isNewsOpen = !this.isNewsOpen
      if (this.isNewsOpen) {
        this.$emit('open-news', 24)
      }
    },
    mark () {
      this.isNewsOpen = false
      this.$emit('read-news', this.id)
    }
    // unmark(){
    //   this.$emit('unmark',this.id)
    // }
  },
  components: {
    AppButton,
    AppNewsList
  }
}
</script>

<style scoped>

</style>
