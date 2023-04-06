<template>
    <q-header class="header bg-black">
      <!-- 3333 -->
      <div class="text-grey">

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
const {
  mapState: mapSettingState,
  mapActions: mapSettingActions
} = createNamespacedHelpers('setting')
console.log(createNamespacedHelpers('setting'));
export default {
  data(){
    return{
      isShow:false
    }
  },
  computed:{
    ...mapSettingState(['isSideBarShow'])
  },
  methods:{
    showAndHide: function(){
      console.log(this.isSideBarShow);
      this.$store.commit('setting/click_tabs_side',!this.isSideBarShow)
      console.log(this.isSideBarShow);

      
    },
  }
}
</script>
<style scoped lang="scss">
.text-grey{
  float: right;
  padding: 0 20px;
  margin: 10px 0;
  
}
</style>
