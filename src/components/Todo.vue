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
            v-model="newTodo.input"
          />
          <!-- <v-btn icon ripple>
            <v-icon color=newTodo.color ?: >folder</v-icon>
          </v-btn> -->
          <v-btn icon ripple>
            <v-menu>
              <template v-slot:activator="{ on }">
                <v-icon color="grey lighten-1" v-on="on">event</v-icon>
              </template>
              <v-date-picker v-model="newTodo.datetime" no-title scrollable>
                <v-btn flat color="primary" @click="menu = false">Cancel</v-btn>
                <v-btn flat color="primary" @click="$refs.menu.save(newTodo.datetime)">OK</v-btn>
              </v-date-picker>
            </v-menu>
          </v-btn>
          <span class="text-sm-left">{{newTodo.datetime}}</span>
          <v-btn icon ripple>
            <v-icon color="grey lighten-1">account_circle</v-icon>
          </v-btn>
          <span class="text-sm-left">{{newTodo.asignee}}</span>
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
              <v-checkbox v-model="item.flag"/>
            </v-list-tile-action>
            <v-list-tile-avatar>
              <v-icon :class="[item.color]">{{ item.icon }}</v-icon>
            </v-list-tile-avatar>

            <v-list-tile-content>
              <v-list-tile-title>{{ item.todo }}</v-list-tile-title>
              <v-list-tile-sub-title>{{ item.datetime }}</v-list-tile-sub-title>
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
    data: () => ({
        items: [
          { flag : true, icon: 'folder', color: '', todo: 'Photos', datetime: 'Jan 9, 2014', asignee : 'takeshi' },
          { flag : false, icon: 'folder', color: '', todo: 'Recipes', datetime: 'Jan 17, 2014', asignee : 'takeshi' },
          { flag : true, icon: 'folder', color: '', todo: 'Work', datetime: 'Jan 28, 2014', asignee : 'takeshi' }
        ],
        newTodo : {
          flag : false,
          todo : "",
          icon : "folder",
          color : "",
          datetime : "",
          asignee : ""
        }
    }),
    methods: () => ({

    })
  }
</script>

<style>

</style>
