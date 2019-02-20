<template>
    <ul class="list-group">

        <li class="list-group-item" v-for="item in items" :key="item.id">

                {{item.title}} - $ {{item.price}}

                <button @click="$emit('remove-from-cart', item)" class="btn badge badge-danger float-right">Remove from the Cart</button>

        </li>

        <div v-if="items.length > 0" class="card">
            <h4 class="text-center">Total $ {{ total }}</h4>
        </div>

        <button @click="$emit('pay')" v-if="items.length > 0" :disabled="items.length === 0" class="btn btn-info my-3">Pay Now</button>

    </ul>
</template>

<script>
export default {
    props: ['items'],

    computed: {
        total() {

            return this.items.reduce((acc, item) => acc + Number(item.price), 0);
        }
    }
}
</script>

