<template>
<div class="chat__photo">
      <div class="chat__photo-block">
    <h2 class="chat__photo-title">Отправить картинку</h2>
    <div class="chat__photo-inputs">
    <label class="chat__photo-label">
        <span class="chat__photo-span" placeholder="URL">URL</span>
        <input type="text" class="chat__photo-input">
    </label>
    <label class="chat__photo-label">
        <span class="chat__photo-span" placeholder="Комментарий">Комментарий</span>
        <textarea class="chat__photo-input"></textarea>
    </label>
    </div>
    <div class="chat__photo-btns">
        <button class="chat__photo-btn cancel" @click="closeModal()">Отмена</button>
        <button class="chat__photo-btn send">Отправить</button>
    </div>
  </div>
</div>
</template>

<script>
export default {
    props: {
        modalWindow: Boolean
    },
    methods: {
        closeModal(){
            this.$emit("closeModal");
        }
    }
}
</script>
