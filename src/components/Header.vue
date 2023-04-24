<template>
    <q-header class="header bg-black">
      <!-- 3333 -->
      <div class="text-grey show-left" >
        <q-btn
        icon='pageview'
              dense
              flat
              round
              class='fab-icon cursor-pointer material-icons-round '
              size='md'
              color='#26A69A'
              v-ripple
              @click="showAndHideSearch"
              key='format_align_center'
            />
      </div>
      
      <div class="text-grey show-hide">

        <!-- <div>{{ store.counter  }} {{counter }}</div> -->
        <q-btn
              icon='table_chart'
              dense
              flat
              round
              class='fab-icon cursor-pointer material-icons-round'
              size='md'
              color='#26A69A'
              v-ripple
              @click="showAndHide"
              key='format_align_center'
            />
      </div>
    </q-header>
</template>

<script>
import { createNamespacedHelpers } from 'vuex'
import { getUserInfo } from 'src/api/setting'
const {
  mapState: mapSettingState,
  mapActions: mapSettingActions
} = createNamespacedHelpers('setting')
export default {
  data(){
    return{
      isShow:false
    }
  },
  computed:{
    ...mapSettingState(['isSideBarShow','isShowSearch'])
  },
  created(){
    this.getUserInfoData()
  },
  methods:{
    showAndHide: function(){
      this.$store.commit('setting/click_tabs_side',!this.isSideBarShow)   
    },
    async getUserInfoData(){
      await getUserInfo('/list/risk').then(res=>{
        console.log(res);
      })
    },
    showAndHideSearch(){
      this.$store.commit('setting/click_toogle_search', !this.isShowSearch)
    }
  }
}
</script>
<style scoped lang="scss">
.show-left{
  float: left;
  padding: 0 20px;
  margin: 10px 0;
}
.show-hide{
  float: right;
  padding: 0 20px;
  margin: 10px 0;
  
}
</style>
