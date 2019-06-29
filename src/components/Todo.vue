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
          @submit.prevent="addTodo"
        >
          <v-text-field
            @click:append="addTodo"
            append-icon="edit"
            label="Put Your Todo!"
            single-line
            outline
            hide-details
            v-model="newTodo.todo"
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
                <v-btn flat color="primary" @click="newTodo.datetime = ''">Delete</v-btn>
                <v-btn flat color="primary" @click="menu = false">Cancel</v-btn>
                <v-btn flat color="primary" @click="$refs.menu.save(newTodo.datetime)">OK</v-btn>
              </v-date-picker>
            </v-menu>
          </v-btn>
          <span class="text-sm-left">{{newTodo.datetime}}</span>
          <v-btn icon ripple>
            <v-menu>
              <template v-slot:activator="{ on }">
                <v-icon color="grey lighten-1" v-on="on">account_circle</v-icon>
              </template>
              <v-text-field solo append-icon="edit" hide-details v-model="newTodo.category" @click.stop=""/> 
            </v-menu>
          </v-btn>
          <span class="text-sm-left">{{newTodo.category}}</span>
        </v-form>
        <hr>
        <v-list two-line subheader>
          <v-list-tile
            v-for="(item, index) in items"
            :key="index"
            avatar
            @click=""
          >
            <v-list-tile-action>
              <v-checkbox v-model="item.flag"/>
            </v-list-tile-action>
            <!-- <v-list-tile-avatar>
              <v-icon :class="[item.color]">{{ item.icon }}</v-icon>
            </v-list-tile-avatar> -->

            <v-list-tile-content>
              <v-list-tile-title>{{ item.todo }}</v-list-tile-title>
              <v-list-tile-sub-title>{{ item.datetime }}</v-list-tile-sub-title>
            </v-list-tile-content>

            <v-list-tile-action>
              <v-list-tile-action-text>{{ item.category }}</v-list-tile-action-text>
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
          { flag : true, icon: 'folder', color: '', todo: '授業の準備', datetime: '2019-06-30', category : '学校' },
          { flag : false, icon: 'folder', color: '', todo: '夏休みの宿題', datetime: '2019-08-31', category : '学校' },
          { flag : true, icon: 'folder', color: '', todo: '海に行く', datetime: '2019-07-20', category : '約束' }
        ],
        newTodo : {
          flag : false,
          todo : "",
          icon : "folder",
          color : "",
          datetime : "",
          category : ""
        }
    }),
    methods: {
      addTodo: function () {
        const addTodo = Object.assign({}, this.newTodo);
        this.items.push(addTodo)
        this.newTodo = {
          flag : false,
          todo : "",
          icon : "folder",
          color : "",
          datetime : "",
          category : ""
        }
      }
    }
  }
</script>

<style>

</style>
