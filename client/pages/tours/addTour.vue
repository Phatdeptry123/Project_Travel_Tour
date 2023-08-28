<template>
    <div class="mt4">
        <h1>Thêm Tour Mới</h1>
        <form @submit="addTour">
            <div class="mb-3">
                <label for="name" class="form-label">Tên Tour</label>
                <input v-model="formData.name" type="text" class="form-control" id="name" name="name">
            </div>
            <div class="mb-3">
                <label for="description" class="form-label">Mô tả</label>
                <input v-model="formData.description" type="text" class="form-control" id="description" name="description">
            </div>
            <div class="mb-3">
                <label for="image" class="form-label">Hình Ảnh</label>s
                <input v-model="formData.image" type="text" class="form-control" id="image" name="image">
            </div>
            <div class="mb-3">
                <label for="level" class="form-label">Cấp Độ</label>
                <input v-model="formData.level" type="text" class="form-control" id="level" name="level">
            </div>
            <button type="submit" class="btn btn-primary">Thêm</button>
        </form>
    </div>
</template>

<script setup>

const formData = ref({
    name: '',
    description: '',
    image: '',
    level: '',
})

const runtimeConfig = useRuntimeConfig()
const addTour = async (event) => {
    event.preventDefault();
    const { data: tours } = await useFetch(`${runtimeConfig.public.apiBase}/tours/create`, { method: 'post', body: formData.value })
    alert("Thêm Thành Công")
}

</script>

<style></style>