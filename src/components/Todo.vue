<template>
  <v-layout row >
    <v-flex xs12 sm6 offset-sm3>
      <v-card>
        <v-toolbar color="light-blue" dark>
          <v-toolbar-title>Todo</v-toolbar-title>
        </v-toolbar>
        <v-spacer/>
        <v-form
          ref="form"
          lazy-validation
          @submit.prevent=""
        >
          <v-text-field
            @click:append=""
            append-icon="edit"
            label="Put Your Todo!"
            single-line
            outline
            hide-details
          />
          <v-btn icon ripple>
            <v-icon color="grey lighten-1">event</v-icon>
          </v-btn>
          <v-btn icon ripple>
            <v-icon color="grey lighten-1">folder</v-icon>
          </v-btn>
          <v-btn icon ripple>
            <v-icon color="grey lighten-1">account_circle</v-icon>
          </v-btn>
          <span class="text-sm-left">takeshi</span>
        </v-form>
        <hr>
        <v-list two-line subheader>
          <v-list-tile
            v-for="item in items"
            :key="item.title"
            avatar
            @click=""
          >
            <v-list-tile-action>
              <v-checkbox v-model="sound"/>
            </v-list-tile-action>
            <v-list-tile-avatar>
              <v-icon :class="[item.iconClass]">{{ item.icon }}</v-icon>
            </v-list-tile-avatar>

            <v-list-tile-content>
              <v-list-tile-title>{{ item.title }}</v-list-tile-title>
              <v-list-tile-sub-title>{{ item.subtitle }}</v-list-tile-sub-title>
            </v-list-tile-content>

            <v-list-tile-action>
              <v-list-tile-action-text>{{ item.asignee }}</v-list-tile-action-text>
              <v-btn icon ripple>
                <v-icon color="grey lighten-1">delete</v-icon>
              </v-btn>
            </v-list-tile-action>
          </v-list-tile>
        </v-list>
      </v-card>
    </v-flex>
  </v-layout>
</template>

<script>
  export default {
    data () {
      return {
        items: [
          { icon: 'folder', iconClass: 'red', title: 'Photos', subtitle: 'Jan 9, 2014', asignee : 'takeshi' },
          { icon: 'folder', iconClass: 'indigo', title: 'Recipes', subtitle: 'Jan 17, 2014', asignee : 'takeshi' },
          { icon: 'folder', iconClass: '#123456', title: 'Work', subtitle: 'Jan 28, 2014', asignee : 'takeshi' }
        ]
      }
    }
  }
</script>

<style>

</style>
