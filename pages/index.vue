<template>
  <div class="container-fluid">
    <div class="row my-5">
      <div class="col-lg-6">
        <nuxt-link to="/pengunjung/tambah">
          <div class="card bg-pengunjung rounded-5 mt-5">
            <div class="card-body">
              <h2>Pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>

      <div class="col-lg-6">
        <nuxt-link to="/buku">
          <div class="card bg-buku rounded-5 mt-5">
            <div class="card-body">
              <h2>Cari Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
      <div class="statistik rounded mb-7">
        <h1 class="ps-0 pt-5 ms-5">STATISTIK</h1>
      </div>

      <div class="col-lg-6">
        <nuxt-link to="/pengunjung">
          <div class="card pengunjung rounded-5 mt-5">
            <div class="card-body text">
              <h1 class="ps-5">{{ hasilp }}</h1>
              <h2 class="pt-5 ps-5">Pengunjung</h2>
            </div>
          </div>
        </nuxt-link>
      </div>

      <div class="col-lg-6">
        <nuxt-link to="/buku">
          <div class="card buku rounded-5 mt-5">
            <div class="card-body text">
              <h1 class="ps-5">{{ hasilb }}</h1>
              <h2 class="pt-5 ps-4">Buku</h2>
            </div>
          </div>
        </nuxt-link>
      </div>
    </div>
  </div>

  <div class="row mt-3">
    <div class="col-lg-6">
      <div class="card-body">
        <Bar :options="chartOptions" :data="chartData"></Bar>
      </div>
    </div>
  </div>
</template>
<script>
import { Bar } from "vue-chartjs";
import { Chart as ChartJS, Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale } from "chart.js";
ChartJS.register(Title, Tooltip, Legend, BarElement, CategoryScale, LinearScale);

export default {
  name: "BarChart",
  components: { Bar },
  data() {
    return {
      chartData: {
        labels: ["January", "February", "March", "April", "May", "June", "July", "August", "September", "October", "November", "December"],
        datasets: [
          {
            label: "",
            data: [80, 20, 60, 25, 45, 17, 55, 100, 59, 35, 25, 79],
            backgroundColor: ["#3accfa"],
          },
        ],
      },
      chartOptions: {
        responsive: true,
        maintainAspectRatio: false,
        aspectRatio: 0.9,
      },
    };
  },
};
</script>

<style scoped>
.card {
  height: 250px;
  box-shadow: 1px 1px 10px #424242;
}
.card.bg-pengunjung {
  background-image: url("../assets/img/caribuku.webp");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  color: #0c0101;
}
.card.bg-buku {
  background-image: url("../assets/img/kunjungan.webp");
  background-repeat: no-repeat;
  background-position: center center;
  background-size: cover;
  color: #0c0101;
}

.card.pengunjung {
  background-color: #f3eebb;
}
.card.buku {
  background-color: #c5fbc0;
}
.text {
  display: flex;

  align-items: center;
}
.text > h1 {
  font-size: 7rem;
}
/* .card {
  width: 50%;
  margin-left: 20%;
} */
</style>

<script setup>
useHead({
  title: "PERPUS DIGITAL",
  meta: [
    {
      name: "description",
      content: "Halaman buku",
    },
  ],
});
const supabase = useSupabaseClient();

const hasilp = ref(0);

const hasilb = ref(0);

const pengunjung = async () => {
  const { data, error, count } = await supabase.from("pengunjung").select("*", { count: "exact" });
  if (count) hasilp.value = count;
};

const buku = async () => {
  const { data, error, count } = await supabase.from("buku").select("*", { count: "exact" });
  if (count) hasilb.value = count;
};

onMounted(() => {
  pengunjung();
  buku();
});
</script>
