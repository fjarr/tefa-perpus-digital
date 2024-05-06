<template>
    <div class="container-fluid">
        <div v-if="loading" class="d-flex justify-content-center">
            <div class="loader"></div>
        </div>
        <div v-else>
            <table style="margin-left: 2%;">
                <tr class="text-center">
                    <td colspan="4">
                        <h1 style="font-family: inter">DETAIL BUKU</h1>
                    </td>
                </tr>
                <tr>
                    <td rowspan="7"><img :src="buku.cover" class="cover" alt="cover" /></td>
                </tr>
                <tr>
                    <td class="ps-5">JUDUL</td>
                    <td class="ps-3">:</td>
                    <td class="ps-3">{{ buku.judul }}</td>
                </tr>
                <tr>
                    <td class="ps-5">PENULIS</td>
                    <td class="ps-3">:</td>
                    <td class="ps-3">{{ buku.penulis }}</td>
                </tr>
                <tr>
                    <td class="ps-5">PENERBIT</td>
                    <td class="ps-3">:</td>
                    <td class="ps-3">{{ buku.penerbit }}</td>
                </tr>
                <tr>
                    <td class="ps-5">KATEGORI</td>
                    <td class="ps-3">:</td>
                    <td class="ps-3">{{ buku.kategori.nama }}</td>
                </tr>
                <tr>
                    <td class="ps-5">RAK</td>
                    <td class="ps-3">:</td>
                    <td class="ps-3">{{ buku.rak.kode }}</td>
                </tr>
                <tr>
                    <td class="ps-5">DESKRIPSI</td>
                    <td class="ps-3">:</td>
                    <td class="ps-3">{{ buku.deskripsi }}</td>
                </tr>
                <tr colspan="4">
                    <td style="padding-left:2%;">
                        <nuxt-link to="../buku">
                            <div class="input-group text-center mt-4 ">
                                <button type="button" class="btn btn-outline-primary rounded-4 ">
                                    KEMBALI
                                </button>
                            </div>
                        </nuxt-link>
                    </td>
                </tr>
            </table>
        </div>
    </div>
</template>


<script setup>
useHead({ title: "detailbuku" })
const supa = useSupabaseClient()
const route = useRoute()
const buku = ref({})
const loading = ref(true)

const getBookById = async () => {
    loading.value = true
    const { data, error } = await supa.from('buku').select(`*, kategori(*), rak(*)`)
        .eq('id', route.params.id)
    if (data) {
        console.log(data[0])
        buku.value = data[0]
        loading.value = false
    }
}

onMounted(() => {
    getBookById()
})
</script>

<style scoped>
.loader {
    border: 16px solid #f3f3f3;
    border-radius: 50%;
    border-top: 16px solid blue;
    border-bottom: 16px solid blue;
    width: 100px;
    height: 100px;
    -webkit-animation: spin 2s linear infinite;
    animation: spin 2s linear infinite;
}

@-webkit-keyframes spin {
    0% {
        -webkit-transform: rotate(0deg);
    }

    100% {
        -webkit-transform: rotate(360deg);
    }
}

@keyframes spin {
    0% {
        transform: rotate(0deg);
    }

    100% {
        transform: rotate(360deg);
    }
}

img {
    width: 300px;
    height: 400px;
}

button {
    text-align: center;
    color: black;
    font-family: inter;
}
table{
    font-size: 30px;
}
@media only screen and (max-width: 820px) {
    .loader {
        border: 16px solid #f3f3f3;
        border-radius: 50%;
        border-top: 16px solid blue;
        border-bottom: 16px solid blue;
        width: 10px;
        height: 10px;
        -webkit-animation: spin 2s linear infinite;
        animation: spin 2s linear infinite;
    }

    @-webkit-keyframes spin {
        0% {
            -webkit-transform: rotate(0deg);
        }

        100% {
            -webkit-transform: rotate(360deg);
        }
    }

    @keyframes spin {
        0% {
            transform: rotate(0deg);
        }

        100% {
            transform: rotate(360deg);
        }
    }

    img {
        width: 100%;
        height: auto;
    }

    table {
        font-size: 5px;
    }

    button {
        text-align: center;
        width: 40px;
        height: 20px;
        font-size: 5px;
        color: black;
        font-family: inter;
    }
}
</style>