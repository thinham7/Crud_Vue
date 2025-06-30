<script setup>
defineModel('dienThoai', {
    default: () => ({
        ten: '',
        hang: 'apple',
        dung_luong: '64GB',
        gia: 0
    }),
})
</script>
<template>
    Tên: <input type="text" v-model="dienThoai.ten"> <br>
    Hãng: <select name="hang" id="hang" v-model="dienThoai.hang">
        <option value="Apple">Apple</option>
        <option value="Samsung">Samsung</option>
        <option value="Xiaomi">Xiaomi</option>
        <option value="Oppo">Oppo</option>
        <option value="Vivo">Vivo</option>
    </select>
    <br>
    Dung Lượng: <select name="dung_luong" id="dung_luong" v-model="dienThoai.dung_luong">
        <option value="64GB">64GB</option>
        <option value="128GB">128GB</option>
        <option value="256GB">256GB</option>
        <option value="512GB">512GB</option>
    </select>
    <br>
    Giá: <input type="number" placeholder="Nhập giá" name="gia" id="gia" v-model="dienThoai.gia"  > <br>
</template>