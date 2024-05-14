<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">Cari Buku</h2>
        <div class="my-3">
          <form @submit.prevent="getBooks">
            <input v-model="keyword" type="search" class="form-control rounded-5" placeholder="Mau baca apa hari ini" />
          </form>
        </div>
        <div class="my-3 text-muted">menampilkan {{ books.length }} dari {{ hasil }}</div>
        <div class="row">
          <div v-for="(book, i) in books" :key="i" class="col-lg-2">
            <nuxt-link :to="`buku/${book.id}`">
              <div class="card mb-3">
                <div class="card-body">
                  <img :src="book.cover" class="cover" alt="cover" />
                </div>
              </div>
            </nuxt-link>
          </div>
        </div>
      </div>
    </div>
  </div>
  <div class="d-flex justify-content-end">
    <NuxtLink to="/" class="btn btn-secondary btn-lg rounded-2 px-5">Kembali</NuxtLink>
  </div>
</template>

<script setup>
useHead({
  title: "PERPUS DIGITAL",
  meta: [
    {
      name: "description",
      content: "Halaman Detail Buku",
    },
  ],
});
const keyword = ref("");

const supabase = useSupabaseClient();

const hasil = ref([]);

const books = ref([]);
const getBooks = async () => {
  const { data, error } = await supabase.from("buku").select(`*, kategori(*)`).ilike("judul", `%${keyword.value}%`);
  if (data) books.value = data;
};

const hasilBuku = async () => {
  const { data, count } = await supabase.from("buku").select(`*`, { count: "exact" });
  if (data) hasil.value = count;
};

onMounted(() => {
  getBooks();
  hasilBuku();
});
</script>

<style scoped>
.card-body {
  width: 100%;
  height: 20 rem;
  padding: 0;
  box-shadow: 1px 1px 10px #403610 !important;
}
.cover {
  width: 100%;
  height: 100%;
  object-fit: cover;
  object-position: 0;
}
.btn-warning {
  box-shadow: 1px 1px 10px #403610 !important;
}
</style>
