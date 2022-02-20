<template>
    <div>
        <h3 class="text-center">Alışveriş Listesi</h3>
        <div class="mb-2">
            <input type="text" placeholder="ne alacaksın ?" @keydown.enter="onSave">
        </div>
    </div>
</template>

<script>
export default {
    inject : ["onSave"]
}
</script>