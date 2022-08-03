<template>
<div class="chat__photo">
      <div class="chat__photo-block">
    <h2 class="chat__photo-title">Отправить картинку</h2>
    <div class="chat__photo-inputs">
    <label class="chat__photo-label">
        <span class="chat__photo-span" placeholder="URL">URL</span>
        <input type="text" class="chat__photo-input" v-model="imageUrl">
    </label>
    <label class="chat__photo-label">
        <span class="chat__photo-span" placeholder="Комментарий">Комментарий</span>
        <textarea class="chat__photo-input" v-model="imageCaption"></textarea>
    </label>
    </div>
    <div class="chat__photo-btns">
        <button class="chat__photo-btn cancel" @click="closeModal()">Отмена</button>
        <button class="chat__photo-btn send" @click="addImage();closeModal()">Отправить</button>
    </div>
  </div>
</div>
</template>

<script>
export default {
    props: {
        modalWindow: Boolean,
        userId: Number,
    },
    methods: {
        closeModal(){
            this.$emit("closeModal");
        },
        addImage(){
            const image = {
                userId: this.userId,
                url: this.imageUrl,
                userText: this.imageCaption,
                date: new Date().toLocaleTimeString(navigator.language, {hour: '2-digit', minute:'2-digit'})
            }
            this.$emit("addImage", image);
            this.imageUrl = this.imageCaption = '';
        },
    },
    data(){
        return {
            imageUrl: '',
            imageCaption: ''
        }
    }
}
</script>
