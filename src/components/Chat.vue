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

              </div>
              <div class="chat__item-input">
                  <textarea class="chat__item-input-text" placeholder="Написать сообщение..." v-model="item.text"></textarea>
                  <button v-if="item.text.length > 0"><img src="@/assets/images/icons/send.svg" alt="" ></button>
                  <button v-else-if="item.text == ''" @click="modalWindow = true"><img src="@/assets/images/icons/photo.svg" alt=""></button>
              </div>
            </div>
          </div>
      </div>
      <Modal 
      v-if="modalWindow == true"
      :modalWindow="modalWindow"
      @closeModal="modalWindow = false"/>
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
  },
  data(){
    return {
    }
  }
}


</script>
