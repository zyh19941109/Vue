<template>
  <div id="app">
    <!-- <div id="nav">
                                                              <router-link to="/">Home</router-link> |
                                                              <router-link to="/about">About</router-link>
                                                            </div> -->
    <!-- <router-view></router-view> -->
    <h3 @click="modal">模态框</h3>
    <h3 @click="action">动作面板</h3>
    <Modal ref="Modal" title="确认信息" message="你确定要这样做吗？" @z-modal-cancel="handleModalCancel" @z-modal-ok="handleModalOk"></Modal>
    <Actions ref="Action" :actions="actions" @z-action-cancel="handleActionCancel" @z-action-ok="handleActionOk"></Actions>
    <h3 @click="onReserve">预约时间:{{reserveTime}}</h3>
    <PickerTime ref="PickerTime" :yyDay="7" :startHour="8" :endHour="22" startTime="2020-04-20" @handleOk="handleOk" @handleCancel="handleCancel"></PickerTime>
    <Switchs title="switch开关" :defaultChecked="false" :disabled="false" @z-switch="handleSwitch"></Switchs>
    <Options :optionsList="optionsList"></Options>
    <ScrollView :scrollList="scrollList" @handleSelect="handleSelect"></ScrollView>
    <Suspend @handleClick="handleClick">
      <img src="./assets/logo.png" alt="">
    </Suspend>
  </div>
</template>
<script>
  import Modal from './MobileModal/index';
  import Actions from './MobileAction/index';
  import Switchs from './MobileSwitch/index';
  import PickerTime from './PickerTime/index';
  import Options from './Options/index';
  import ScrollView from './ScrollView/index';
  import Suspend from './Suspend/index'
  export default {
    data() {
      return {
        actions: [{
          text: '操作一'
        }, {
          text: '操作二'
        }, {
          text: '操作三'
        }],
        reserveTime: '立即配送', //默认方式
        scrollList: ['选项1', '选项2', '选项3', '选项4', '选项5', '选项6', '选项7', '选项8'],
        optionsList: [{
          // iconClass: 'z-icon-default',
          text: '111'
        }, {
          iconClass: 'z-icon-default',
          text: '222'
        }, {
          iconClass: 'z-icon-default',
          text: '333'
        }]
      }
    },
    created() {},
    mounted() {},
    methods: {
      modal() {
        this.$refs.Modal.showModal()
      },
      handleModalCancel(val) {
        console.log(val)
        this.$refs.Modal.hideModal()
      },
      handleModalOk(val) {
        console.log(val)
        this.$refs.Modal.hideModal()
      },
      action() {
        this.$refs.Action.showAction()
      },
      handleActionCancel(val) {
        console.log(val)
        this.$refs.Action.hideAction()
      },
      handleActionOk(val) {
        console.log(val)
        this.$refs.Action.hideAction()
      },
      handleSwitch(val) {
        console.log(val)
      },
      onReserve() {
        this.$refs.PickerTime.showTimeModel()
      },
      handleOk(val) {
        console.log(val)
        this.reserveTime = val.value;
        this.$refs.PickerTime.modelCancel()
      },
      handleCancel(val) {
        console.log(val)
        this.$refs.PickerTime.modelCancel()
      },
      handleSelect(val) {
        console.log(val)
      },
      handleClick(){
        alert('hello')
      }
    },
    components: {
      Modal,
      Actions,
      Switchs,
      PickerTime,
      Options,
      ScrollView,
      Suspend,
    },
    computed: {},
    watch: {}
  }
</script>
<style lang="less">
  * {
    margin: 0;
    padding: 0;
  }
  #app {
    font-family: 'Avenir', Helvetica, Arial, sans-serif;
    -webkit-font-smoothing: antialiased;
    -moz-osx-font-smoothing: grayscale;
    color: #2c3e50;
  }
  #nav {
    padding: 30px;
    a {
      font-weight: bold;
      color: #2c3e50;
      &.router-link-exact-active {
        color: #42b983;
      }
    }
  }
  h3 {
    font-size: 26px;
    color: #333;
    margin-top: 30px;
    text-align: center;
  }
</style>
