<template>
  <v-container>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="12">
        <div class="text-center">
          <v-img
            src="https://placehold.jp/851x315.png"
            lazy-src="https://placehold.jp/851x315.png"
          ></v-img>
        </div>
        <div class="pa-2">
          <h1>{{ $t('chapter') }}</h1>
          <div>
            <v-tooltip v-for="(item, key) in config.social" :key="key" bottom>
              <template v-slot:activator="{ on, attrs }">
                <v-btn
                  icon
                  :href="item.link"
                  target="_blank"
                  v-bind="attrs"
                  v-on="on"
                >
                  <v-icon>{{ item.icon }}</v-icon>
                </v-btn>
              </template>
              <span>{{ item.name }}</span>
            </v-tooltip>
          </div>
          <p>{{ $t('index.chapterDetail') }}</p>
        </div>
        <div class="text-center">
          <a :href="$t('index.joinUsLink')" target="_blank">
            <v-btn color="primary">{{ $t('index.joinUsText') }}</v-btn>
          </a>
        </div>
      </v-col>
    </v-row>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="12">
        <h2 class="secondary--text">Events</h2>
      </v-col>
      <v-col cols="12" xs="12" sm="6" md="4">
        <EventCard :event-data="eventData" />
      </v-col>
      <v-col cols="12" xs="12" sm="6" md="4">
        <EventCard :event-data="eventData" />
      </v-col>
      <v-col cols="12" xs="12" sm="6" md="4">
        <EventCard :event-data="eventData" />
      </v-col>
    </v-row>
    <v-row justify="center" align="center">
      <v-col cols="12" sm="12">
        <v-card>
          <v-card-title class="headline">
            About {{ $t('chapter') }}
          </v-card-title>
          <v-card-text>
            <p style="white-space: pre-line; word-wrap: break-word">
              {{ $t('about.chapterDetail') }}
            </p>
          </v-card-text>
          <v-card-actions>
            <a :href="$t('index.joinUsLink')" target="_blank">
              <v-btn color="primary">{{ $t('index.joinUsText') }}</v-btn>
            </a>
          </v-card-actions>
        </v-card>
      </v-col>
    </v-row>
  </v-container>
</template>

<script>
import config from '~/assets/community.config.json'

export default {
  data: () => ({
    config,
    eventData: {
      title: 'hoge',
      date: '2020/10/01',
      detail:
        'Lorem ipsum dolor sit amet, consectetur adipiscing elit. Curabitur hendrerit id quam iaculis mollis. Vivamus at vehicula nisi. Morbi odio tortor, porta sed elit at, commodo laoreet neque. Morbi molestie rutrum nisl nec commodo. Aliquam fringilla ante urna, quis ornare enim hendrerit varius. Phasellus ligula mi, mattis id odio sit amet, luctus ullamcorper nulla. Duis facilisis finibus dictum. Pellentesque ut nisi gravida, condimentum augue et, scelerisque purus. Mauris ornare elementum varius. Cras lobortis interdum neque ullamcorper ultricies. Quisque eget massa fringilla, vulputate felis in, condimentum dolor.',
      link: 'https://',
    },
  }),
  head() {
    return {
      title: 'Home',
      meta: [
        {
          hid: 'description',
          name: 'description',
          content: this.$i18n.t('index.chapterDetail'),
        },
      ],
    }
  },
}
</script>
