<template>
    <!-- click event is modified to only close when the backdrop is clicked not the modal itself-->
    <div class="backdrop" @click.self="closeModal">
        <!-- the modal has a dynamic class if the theme prop is equal to sale -->
        <div class="modal" :class="{ sale: theme === 'sale' }">
            <!-- default slot in case we do not pass anything -->
            <slot>text in case u didn't slot anything</slot>
            <div class="actions">
                <!-- named slot -->
                <slot name="links"></slot>
            </div>
        </div>
    </div>
</template>

<script>
export default {
    props: ['theme'],
    methods: {
        // emit a custom event to close the modal
        closeModal() {
            this.$emit('close');
        }
    }
}
</script>

<!-- can be scoped like this <style scoped> -->
<style>
.modal {
    width: 400px;
    padding: 20px;
    margin: 100px auto;
    background: white;
    border-radius: 10px;
}

.backdrop {
    top: 0;
    position: fixed;
    background: rgba(0, 0, 0, 0.5);
    width: 100%;
    height: 100%;
}

h1 {
    color: #03cfb4;
    border: none;
    padding: 0;
}

p {
    font-style: normal;
}

.modal .actions {
    text-align: center;
    margin: 30px 0 10px 0;
}

.modal .actions a {
    color: #333;
    padding: 8px;
    border: 1px solid #eee;
    border-radius: 4px;
    text-decoration: none;
    margin: 10px;
}

.modal.sale {
    background: crimson;
    color: white;
}

.modal.sale h1 {
    color: white;
}

.modal.sale .actions {
    color: white;
}

.modal.sale .actions a {
    color: white;
}
</style>