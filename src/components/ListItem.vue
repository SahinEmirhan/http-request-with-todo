<template>
    <div>
        <ul v-if="listObject.itemList.length > 0">
            <li v-for="item in listObject.itemList" :key="item.id" class="justify-content-between align-items-center d-flex">
                <span>{{item.title}}</span>
                <button @click="onDelete(item)" class="sm red">Sil</button>
            </li>
        </ul>
        <div v-else class="bg-blue text-white">
        Herhangi Bir Ürün Yoktur..
        </div>
        <small v-if="listObject.itemList.length > 0" class="text-red d-flex justify-content-end mt-2">{{listObject.itemList.length}} tane alınacak ürün vardır..</small>
    </div>
</template>

<script>
export default {
    inject: ['listObject','onDelete']
}
</script>