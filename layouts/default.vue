<template>
  <v-app light>
    <v-navigation-drawer
      v-model="drawer"
      :mini-variant="miniVariant"
      :clipped="clipped"
      fixed
      color="#FFFFFF"
      app
    >
      <v-list class="blue--text">
        <v-list-item
          v-for="(item, i) in items"
          :key="i"
          :to="item.to"
          router
          exact
        >
          <v-list-item-action>
            <v-icon color="#031C4E">{{ item.icon }}</v-icon>
          </v-list-item-action>
          <v-list-item-content class="black--text">
            <v-list-item-title v-text="item.title" />
          </v-list-item-content>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>
    <v-app-bar
      :clipped-left="clipped"
      fixed
      app
      style="background-color: #031C4E"
    >
      <v-app-bar-nav-icon @click.stop="drawer = !drawer" />
      <v-toolbar-title v-text="title" />
      <v-spacer />
      <v-btn icon @click.stop="rightDrawer = !rightDrawer">
        <v-icon>mdi-menu</v-icon>
      </v-btn>
    </v-app-bar>
    <v-main
      style="background-color: #F2F2F2; height: 100vh;"
      class="overflow-y-auto"
    >
      <v-container style=" height: 100vh;">
        <nuxt />
      </v-container>
    </v-main>

    <v-navigation-drawer v-model="rightDrawer" :right="right" temporary fixed>
      <v-list>
        <v-list-group>
          <template v-slot:activator>
            <v-list-item-content>
              <v-list-item-title>Logout</v-list-item-title>
            </v-list-item-content>
          </template>

          <v-list-item @click="open()">
            <v-list-item-content>
              <v-list-item-title>
                <div class=" text-center">
                  <v-btn color="green" small @click="logoutDialog = true"
                    >Yes</v-btn
                  >
                  <v-btn color="red" small>No</v-btn>
                </div>
              </v-list-item-title>
            </v-list-item-content>
          </v-list-item>
        </v-list-group>
      </v-list>

      <v-list>
        <v-list-item to="/inspire" exact @click.native="right = !right">
          <v-list-item-action>
            <v-icon color="white" light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Settings</v-list-item-title>
        </v-list-item>
        <v-list-item @click.native="right = !right">
          <v-list-item-action>
            <v-icon color="white" light>
              mdi-repeat
            </v-icon>
          </v-list-item-action>
          <v-list-item-title>Profile</v-list-item-title>
        </v-list-item>
      </v-list>
    </v-navigation-drawer>

    <div class="text--center">
      <v-dialog v-model="logoutDialog" width="500">
        <v-card>
          <v-card-title class="title primary white--text" primary-title>
            Logout
          </v-card-title>
          <v-spacer />
          <v-card-title class="justify-left my-5 mb-3 subtitle-1 transparent">
            Are you sure you want to log out?
          </v-card-title>

          <v-divider></v-divider>

          <v-card-actions>
            <v-spacer></v-spacer>
            <v-btn
              raised
              small
              class="warning text-capitalize"
              @click="logoutDialog = false"
              >No</v-btn
            >
            <v-btn small raised class="primary text-capitalize">Yes</v-btn>
          </v-card-actions>
        </v-card>
      </v-dialog>
    </div>
    <!--    <v-footer :fixed="fixed" app>-->
    <!--      <span>&copy; {{ new Date().getFullYear() }}</span>-->
    <!--    </v-footer>-->
  </v-app>
</template>

<script>
export default {
  data() {
    return {
      clipped: false,
      drawer: false,
      fixed: false,
      logoutDialog: false,
      items: [
        {
          icon: 'mdi-apps',
          title: 'Welcome',
          to: '/'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Inspire',
          to: '/inspire'
        },
        {
          icon: 'mdi-chart-bubble',
          title: 'Base',
          to: '/base'
        }
      ],
      miniVariant: false,
      right: true,
      rightDrawer: false,
      title: 'Trainfall'
    }
  },
  methods: {
    open() {
      console.log('me there.')
    }
  }
}
</script>
