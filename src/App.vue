<template>
    <div class="wrapper">
        <Chat  
        :chatUsers="chatUsers"
        :send="send"
        :modalWindow="modalWindow"/>
    </div>
</template>

<script>

import Chat from '@/components/Chat.vue';

export default {
    components: {
        Chat,
    },
    data(){
        return {
            chatUsers: [{
                id: 1,
                name: 'Жыленкек',
                status: 'Онлайн',
                img: 'ava1.jpg',
                text: '',
            },
            {   
                id: 2,
                name: 'Nilkek',
                status: 'Онлайн',
                img: 'ava2.jpg',
                text: '',
            }],
            modalWindow: false,
        }
    }
}

</script>
