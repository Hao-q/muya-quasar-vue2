<template>
  <div>
    <q-btn
      icon="format_align_center"
      dense
      flat
      round
      class="absolute-top-right fab-icon cursor-pointer material-icons-round"
      size="md"
      color="#26A69A"
      v-ripple
      key="format_align_center"
      style="top:20px; right: 20px"
      @click="noteBtn"
    >
    </q-btn>
    <q-btn
      icon="dashboard"
      dense
      flat
      round
      class="absolute-bottom-right fab-icon cursor-pointer material-icons-round"
      style="bottom: 150px;right: 20px;"
      size="md"
      color="#26A69A"
      v-ripple
      key="wordCount"
    >
      <q-tooltip
        transition-show="fade"
        transition-hide="fade"
        anchor="center left"
        self="center right"
      >
        <div class="text-body2">
          <p>
            {{ '词:1333' }}
          </p>
          <p>
            {{ '字符:233' }}
          </p>
          <p>
            {{ '段落:33' }}
          </p>
        </div>
      </q-tooltip>
    </q-btn>
    <q-btn
      :icon="isSourceMode ? 'assignment' : 'code'"
      dense
      flat
      round
      class="absolute-bottom-right fab-icon cursor-pointer material-icons-round"
      style="bottom: 100px; right: 20px"
      size="md"
      color="#26A69A"
      v-ripple
      key="source_code"
      :title="!isSourceMode ? '源代码模式' : '预览模式'"
      @click="changeMode"
    >
    </q-btn>
    <q-btn
      icon="save"
      class="absolute-bottom-right fab-icon cursor-pointer material-icons-round"
      style="bottom: 50px;right: 20px"
      dense
      flat
      round
      size="md"
      color="#26A69A"
      v-ripple
      title="保存"
      key="save"
    />
    <NoteOutlineDrawer ></NoteOutlineDrawer>
  </div>
</template>

<script>
import NoteOutlineDrawer from './NoteOutlineDrawer.vue'
import { createNamespacedHelpers } from 'vuex'
import bus from '../components/bus'
const {
  mapState: mapSettingState,
  mapActions: mapSettingActions
} = createNamespacedHelpers('setting')
export default {
  name:'RightBtnList',
  components:{
    NoteOutlineDrawer
  },
  data(){
    return{
    }
  },
  computed:{
    ...mapSettingState(['toggleLeftDrawer','isSourceMode'])
  },
  methods:{
    // 切换预览模式
    changeMode: function(){
      this.$store.commit('setting/click_tab_right_mode', !this.isSourceMode)
      console.log(222);
      // bus.$on('muyaData', (params)=>{
      //   console.log(params);
      //   this.
      // })

    },
    // 切换右侧目录窗口
    noteBtn: function(){
      this.$store.commit('setting/click_toggle_left_drawer',!this.toggleLeftDrawer)
    }
  }
}


</script>
