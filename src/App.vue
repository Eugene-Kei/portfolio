<template>
    <v-app>
        <div class="d-flex align-center justify-center fill-height" v-if="loading">
            <v-progress-circular
                    :size="70"
                    color="primary"
                    indeterminate
            ></v-progress-circular>
        </div>
        <v-main v-else class="grey lighten-5">
            <top-banner/>
            <avatar/>
            <skills/>
            <price/>
            <projects/>
            <contacts/>
            <copyright/>
        </v-main>
    </v-app>
</template>

<script>
  import TopBanner from './components/TopBanner'
  import Avatar from './components/Avatar'
  import Skills from './components/Skills'
  import Projects from './components/Projects'
  import Price from './components/Price'
  import Contacts from './components/Contacts'
  import Copyright from './components/Copyright'

  export default {
    name: 'App',
    components: {
      TopBanner,
      Avatar,
      Skills,
      Projects,
      Price,
      Contacts,
      Copyright
    },
    data: () => ({
      loading: true
    }),
    mounted () {
      // Заметил на гитхабе, что изображение вверху страницы может медленно грузиться.
      // В таком случае, сначала виден блок с аватаром, а потом только появляется картинка.
      // Во избежании этого подставляем прелоадер, пока страница не прогрузилась
      window.addEventListener('load', () => {this.loading = false})
    },
  }
</script>