<template>
  <div class="scroll bg-grey-3 full-height">
    <q-scroll-area class="full-height">
      <q-list>
        <q-item clickable v-ripple="{ color: '#212121' }" v-for="(item, index) in listitems" @click="toDetails(item)" :key="index">
          <q-item-section>
            <div @contextmenu="(e) => noteItemContextMenuHandler(e, noteField)" class="sidebar_list">
              <div class='note-item-title' v-html='item.title'></div>

              <div class='note-item-summary text-grey-7' v-html='item.summary'></div>

              <div class='flex justify-between no-wrap overflow-hidden fa-align-center text-grey-7'>
                <span class='text-left note-info-tag'><q-icon name='category' size='17px' /> {{ '文件夹' }}</span>
                <span class='text-right note-info-tag'><q-icon name='timer' size='17px' /> {{ '2022-1-1' }}</span>
              </div>
            </div>
          </q-item-section>
        </q-item>
      </q-list>
    </q-scroll-area>
    <q-btn  
    style="bottom: 30px;right: 20px;"
     class="absolute-bottom-right fab-btn" 
     size="lg"
     round color="primary"  
     @click="addNoteHandler"
     icon="note_add" >
     <q-tooltip
            anchor="center right"
            self="center left"
            :offset="[10, 10]"
            content-class=" text-white shadow-4  text-h7"
            >创建笔记</q-tooltip>
     </q-btn>
  </div>
</template>

<script>
export default {
  data() {
    return {
      listitems: [{
        title:'标题',
        summary:'在手机上的浏览器里看到有价值的网页时，点击底端的 **分享按钮**，选择 **为知笔记**，网页内容就保存到为知笔记啦！'
      },{
        title:'标题',
        summary:'在手机上的浏览器里看到有价值的网页时，点击底端的 **分享按钮**，选择 **为知笔记**，网页内容就保存到为知笔记啦！'
      },{
        title:'标题',
        summary:'在手机上的浏览器里看到有价值的网页时，点击底端的 **分享按钮**，选择 **为知笔记**，网页内容就保存到为知笔记啦！'
      },{
        title:'标题',
        summary:'在手机上的浏览器里看到有价值的网页时，点击底端的 **分享按钮**，选择 **为知笔记**，网页内容就保存到为知笔记啦！'
      },{
        title:'标题',
        summary:'在手机上的浏览器里看到有价值的网页时，点击底端的 **分享按钮**，选择 **为知笔记**，网页内容就保存到为知笔记啦！'
      },],
    }
  },
  methods: {
    noteItemContextMenuHandler(){

    },
    toDetails(item){
      console.log(item);
    },
    // 创建笔记
    addNoteHandler(){
      console.log(22);
      this.$q
        .dialog({
          title: '创建笔记',
          prompt: {
            model: "新建笔记.md",
            type: 'text',
            attrs: {
              spellcheck: false
            },
            label:"标题"
          },
          ok: '确认',
          cancel: '取消'
        })
        .onOk(data => {
          // this.createNote(data)
        })
    }
  }
}

</script>
<style lang="scss" scoped>
.note-item-title{
  font-size: 18px;
  padding-bottom: 6px;
  font-weight: 900;
  color: #3e3d3d;
}
.note-item-summary{
  padding-bottom: 8px;
}
.sidebar_list{
  padding: 10px 12px;
}
</style>
