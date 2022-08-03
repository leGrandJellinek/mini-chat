<template>
  <div class="chat">
      <div class="chat__container">
          <div class="chat__block">
            <div class="chat__block-item" v-for="item in chatUsers" :key="item.id">
              <div class="chat__item-header">
                <img :src="require(`@/assets/images/${item.img}`)" alt="" class="chat__item-avatar">
                <div class="chat__item-block">
                    <h2 class="chat__item-name">{{item.name}}</h2>
                    <p class="chat__item-status">{{item.status}}</p>
                </div>
              </div>
              <div class="chat__item-main">
                  <div v-for="(msg,index) in usersMsgs" :key="index">
                    <div class="chat__main-item myitem" v-if="msg.userId == item.id">
                      <p class="chat__main-date">{{msg.date}}</p>
                      <div class="chat__main-my-msg" :style="msg.userId == 1 ? 'background: #5074e0;' :'background: #4a4397;'" v-if="msg.url" style="padding:2px; padding-bottom: 10px;"><img :src="msg.url" alt="" class="chat__main-img">{{msg.userText}}</div>
                      <div class="chat__main-my-msg" :style="msg.userId == 1 ? 'background: #5074e0;' :'background: #4a4397;'" v-else>{{msg.userText}}</div>
                    </div>
                    <div class="chat__main-item" v-else>
                      <div class="chat__main-msg" :style="msg.userId == 1 ? 'background: #5074e0;' :'background: #4a4397;'" v-if="msg.url" style="padding:2px; padding-bottom: 10px;"><img :src="msg.url" alt="" class="chat__main-img">{{msg.userText}}</div>
                      <div class="chat__main-msg" :style="msg.userId == 1 ? 'background: #5074e0;' :'background: #4a4397;'" v-else>{{msg.userText}}</div>
                      <p class="chat__main-date">{{msg.date}}</p>
                    </div>
                  </div>
              </div>
              <div class="chat__item-input">
                  <textarea class="chat__item-input-text" placeholder="Написать сообщение..." v-model="item.text"></textarea>
                  <button v-if="item.text.length > 0"  @click="addMessage(item.id,item.text)"><img src="@/assets/images/icons/send.svg" alt="" ></button>
                  <button v-else-if="item.text == ''" @click="forModal(item.id),modalWindow = true"><img src="@/assets/images/icons/photo.svg" alt=""></button>
              </div>
            </div>
          </div>
      </div>
      <Modal 
      v-if="modalWindow == true"
      :modalWindow="modalWindow"
      @closeModal="modalWindow = false"
      :userId="needId"
      @addImage="addImage"/>
  </div>
</template>

<script>

import Modal from "@/components/Modal.vue";

export default {
  components: {
    Modal,
  },
  props: {
    chatUsers: Array,
    modalWindow: Boolean,
    usersMsgs: Array,
  },
  methods: {
    addMessage(id, text){
      text.split(' ').join('') !== '' ?
        this.usersMsgs.push({
        userId: id,
        userText: text,
        date: new Date().toLocaleTimeString(navigator.language, {hour: '2-digit', minute:'2-digit'})
      }) : '';
      this.chatUsers.forEach(el=> el.text = '')
      },
    addImage(image){
      this.usersMsgs.push(image);
    },
    forModal(id){
      return this.needId = id;
    }
  }, 
  data(){
    return {
      needId : 0
    }
  },
}


</script>
