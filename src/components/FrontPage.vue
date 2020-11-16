<template>
  <div class="hello">
    <TopBar :topbar-options="topbarOptions" :search-options="searchOptions" :search-text.sync="searchText" :logo="logo" style="background-color:#DB4C3F"></TopBar>
    <SideBar :compact="true" :primary="false" :menu="menu" ></SideBar>
    <MainSection/>
  </div>
</template>

<script>

import { SideBar, TopBar } from '@e9ine/vue_components'
import MainSection from './MainSection'

export default {
  name: 'FrontPage',
  components: {
    SideBar,
    TopBar,
    MainSection
  },
  data () {
    return {
      menu: [{
        menuItems: [{
          name: 'Inbox 1',
          path: '/avatar',
          icon: 'email'
        },
        {
          name: 'Today',
          path: '/avatar-info',
          icon: 'calendar_today'

        },
        {
          name: 'Upcoming',
          path: '/address-finders',
          icon: 'event',
          expanded: true,
          subItems: [{
            name: 'Projects',
            path: '/address-finders/google-address-finder'

          },
          {
            name: 'Labels',
            path: '/address-finders/google-address-finder'

          },
          {
            name: 'Filters',
            path: '/address-finders/google-address-finder'

          }
          ]
        }]
      }
      ],
      compact: true,
      primary: true,
      searchText: '',
      logo: {
        url: 'https://htmlsigs.s3.amazonaws.com/logos/files/001/087/329/landscape/e9ineLogo.png',
        mobile: true
      },
      searchOptions: {
        placeholder: 'Type to search..',
        clickAction: function () {
          console.log('search clicked')
        },
        mobile: true
      },
      topbarOptions: [
        {
          icon: 'add',
          text: 'Quick Add Task',
          type: 'icon',
          clickAction: function () {
            console.log('new todo')
          }
        },
        {
          icon: 'notifications_none',
          text: 'Notifications',
          type: 'icon',
          pending: false,
          clickAction: function () {
            console.log('notifications')
          },
          mobile: true
        }, {
          icon: 'chat_bubble_outline',
          text: 'Messages',
          type: 'icon',
          clickAction: function () {
            console.log('messages')
          }
        }
      ]
    }
  }
}

</script>

<!-- Add "scoped" attribute to limit CSS to this component only -->
<style scoped lang="scss">

</style>
