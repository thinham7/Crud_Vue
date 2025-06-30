
<template>
    <h1 style="text-align: center;">Quản Lý Điện Thoại</h1>
    <h1 style="text-align: center;">{{ !isUpdate ? 'Thêm' : 'Cập Nhật' }}</h1>
    <FormDienThoai v-model:dienThoai="newDienThoai" />
    <button @click="addDienThoai" v-show="!isUpdate">Thêm Điện Thoại</button>
    <button @click="updateDienThoai" v-show="isUpdate">Cập Nhật Điện Thoại</button>
    <table style="width: 100%; border-collapse: collapse; text-align: center;">
        <thead>
            <tr style="background-color: #f2f2f2;">
                <th style="border: 1px solid #ddd; padding: 8px;">ID</th>
                <th style="border: 1px solid #ddd; padding: 8px;">Tên</th>
                <th style="border: 1px solid #ddd; padding: 8px;">Hãng</th>
                <th style="border: 1px solid #ddd; padding: 8px;">Dung Lượng</th>
                <th style="border: 1px solid #ddd; padding: 8px;">Giá</th>
                <th style="border: 1px solid #ddd; padding: 8px;">Chức Năng</th>
            </tr>
        </thead>
        <tbody>
            <tr v-for="(dt, index) in list" :key="dt.id" style="border: 1px solid #ddd;">
                <td style="border: 1px solid #ddd; padding: 8px;">{{ dt.id }}</td>
                <td style="border: 1px solid #ddd; padding: 8px;">{{ dt.ten }}</td>
                <td style="border: 1px solid #ddd; padding: 8px;">{{ dt.hang }}</td>
                <td style="border: 1px solid #ddd; padding: 8px;">{{ dt.dung_luong }}</td>
                <td style="border: 1px solid #ddd; padding: 8px;">{{ dt.gia }}</td>
                <td style="border: 1px solid #ddd; padding: 8px;">
                    <button @click="editDienThoai(index)" style="margin-right: 5px;">Detail</button>
                    <button @click="deleteDienThoai(index)">Xóa</button>
                </td>
            </tr>
        </tbody>
    </table>
</template>
<script setup>
import { ref } from 'vue';
import FormDienThoai from '../components/FormDienThoai.vue';
const list = ref([
    { id: 1, ten: 'iPhone 14', hang: 'Apple', dung_luong: '128GB', gia: 25000000 },
    { id: 2, ten: 'Galaxy S22', hang: 'Samsung', dung_luong: '256GB', gia: 23000000 },
    { id: 3, ten: 'Redmi Note 11', hang: 'Xiaomi', dung_luong: '64GB', gia: 7000000 },
    { id: 4, ten: 'Reno6', hang: 'Oppo', dung_luong: '128GB', gia: 12000000 },
    { id: 5, ten: 'V21e', hang: 'Vivo', dung_luong: '128GB', gia: 10000000 }
])
const newDienThoai = ref({
    ten: '',
    hang: 'apple',
    dung_luong: '64GB',
    gia: 0
});
const addDienThoai = () => {
    list.value.push({
        id: list.value.length +1,
        ...newDienThoai.value
    })
    resetForm();
}
const deleteDienThoai = (index) => {
    list.value.splice(index, 1);
} 
const resetForm = () => {
    newDienThoai.value = {
        ten: '',
        hang: 'apple',
        dung_luong: '64GB',
        gia: 0
    }
}
const isUpdate = ref(false);
const viTriUpdate = ref(-1);
const editDienThoai = (index) => {
    isUpdate.value = true;
    viTriUpdate.value = index;
    newDienThoai.value = { ...list.value[index] };
}
const updateDienThoai = () => {
    if (viTriUpdate.value >= 0 && viTriUpdate.value < list.value.length) {
        list.value[viTriUpdate.value] = { ...newDienThoai.value };
    }
    resetForm();
    isUpdate.value = false;
    viTriUpdate.value = -1;
}
</script>