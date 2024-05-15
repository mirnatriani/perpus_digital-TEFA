<script setup>
useHead({
  title: "PERPUS DIGITAL",
  meta: [
    {
      name: "description",
      content: "Halaman Riwayat Kunjungan",
    },
  ],
});
const supabase = useSupabaseClient();

const visitors = ref([]);

const keyword = ref([]);

const hasil = ref([]);

const getpengunjung = async () => {
  const { data, error } = await supabase.from("pengunjung").select(`*, keanggotaan(*), keperluan(*)`).ilike("nama", `%${keyword.value}%`).order("id", { ascending: false });
  if (data) visitors.value = data;
};
const hasilPengunjung = async () => {
  const { data, count } = await supabase.from("pengunjung").select(`*`, { count: "exact" });
  if (data) hasil.value = count;
};

onMounted(() => {
  getpengunjung();
  hasilPengunjung();
});
</script>

<template>
  <div class="container-fluid">
    <div class="row">
      <div class="col-lg-12">
        <h2 class="text-center my-4">RIWAYAT KUNJUNGAN</h2>
        <div class="my-3">
          <form @submit.prevent="getpengunjung">
            <input v-model="keyword" type="search" class="form-control form-control-lg rounded-5" placeholder="filter..." />
          </form>
        </div>
        <div class="my-3 text-muted">menampilkan {{ visitors.length }} dari {{ hasil }}</div>
        <table class="table">
          <thead>
            <tr>
              <td>NO</td>
              <td>NAMA</td>
              <td>KEANGGOTAAN</td>
              <td>WAKTU</td>
              <td>KEPERLUAN</td>
            </tr>
          </thead>
          <tbody>
            <tr v-for="(visitor, i) in visitors" :key="i">
              <td>{{ i + 1 }}.</td>
              <td>{{ visitor.nama }}</td>
              <td>{{ visitor.keanggotaan.nama }}</td>
              <td>{{ visitor.tanggal }}, {{ visitor.waktu }}</td>
              <td>{{ visitor.keperluan.nama }}</td>
            </tr>
          </tbody>
        </table>
      </div>
    </div>
  </div>
  <NuxtLink to="/" class="btn btn-secondary btn-lg rounded-2 px-5">Kembali</NuxtLink>
</template>
