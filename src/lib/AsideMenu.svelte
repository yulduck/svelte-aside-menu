<script lang="ts">
  export let isSlideOpened;
  import AsideMenuItem from './AsideMenuItem.svelte';
  import {IMenu} from '../type/MenuType';


  const MENU_ITEMS:IMenu[] = [
    {
      icon: 'MdDeveloperBoard',
      content: 'DashBorad',
      link: '#',
      sub_category:[]
    },
    {
      icon: 'FaCommentDots',
      content: 'Message',
      link: '#',
      sub_category:[]
    },
    {
      icon: 'FaComments',
      content: 'Chat',
      link: '#',
      sub_category:[]
    },
    {
      icon: 'TiChartArea',
      content: 'Challenges',
      link: '#',
      sub_category:[]
    },
    {
      icon: 'FaBookOpen',
      content: 'Classes',
      link: '#',
      sub_category:['Maths', 'English', 'Economics', 'Accounts']
    },
    {
      icon: 'DiTrello',
      content: 'TimeTable',
      link: '#',
      sub_category:[]
    },
  ]
</script>

<ul class="border-y border-white px-1 py-8 mb-6">
  {#each MENU_ITEMS as menu}
    <AsideMenuItem {menu} {isSlideOpened}/> 
  {/each}
</ul>