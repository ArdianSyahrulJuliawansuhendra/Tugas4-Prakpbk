
<template>
  <div>
    <div class="buttons">
      <button @click="filterData('Pelatih')">Pelatih/Mantan Pelatih</button>
      <button @click="filterData('Jersey Kemenangan')">Jersey Kemenangan</button>
      <button @click="filterData('tropi')">Tropi</button>
    </div>
    
    <div class="inf">
      <div 
        v-for="item in filteredData" 
        :key="item.judul" 
        class="card" 
        @click="tampilkanData(item.judul, item.informasi)"
      >
        <span></span>
        <div class="content">
          <img :src="item.gambar" alt="gambar" class="gambar">
        </div>
      </div>
    </div>

    <div v-if="dataTerpilih" class="tampilan-data">
      <h2>{{ dataTerpilih.judul }}</h2>
      <p>{{ dataTerpilih.informasi }}</p>
    </div>
  </div>
</template>

<script>
export default {
  data() {
    return {
      dataTerpilih: null,
      currentFilter: 'Pelatih',
      items: [
        {
          judul: 'Filippo Inzaghi',
          informasi: 'Filippo "Pippo" Inzaghi (lahir 9 Agustus 1973) adalah seorang mantan pemain sepak bola profesional asal Italia yang bermain sebagai penyerang.',
          gambar: 'https://th.bing.com/th/id/OIP.TT8WQ8ulDaxa_g0CYC7b8AHaEs?rs=1&pid=ImgDetMain',
          kategori: 'Pelatih'
        },
        {
          judul: 'Jersey Kemenangan',
          informasi: 'Seragam peringatan Home Stadium edisi terbatas untuk merayakan perebutan gelar liga ke-20 dan perolehan bintang kedua. Di bagian belakang terdapat personalisasi khusus dengan bintang 2 dan angka 20 berwarna emas..',
          gambar: 'src/assets/Screenshot 2024-05-25 001348.png',
          kategori: 'Jersey Kemenangan'
        },
        {
          judul: 'Jersey Kemenangan',
          informasi: 'Seragam peringatan Home Stadium edisi terbatas untuk merayakan perebutan gelar liga ke-20 dan perolehan bintang kedua. Di bagian belakang terdapat personalisasi khusus dengan bintang 2 dan angka 20 berwarna emas.',
          gambar: 'src/assets/Screenshot 2024-05-25 001642.png',
          kategori: 'Jersey Kemenangan'
        },
        {
          judul: 'Luciano Spalletti',
          informasi: 'luciano Spalletti (pelafalan dalam bahasa Italia: [luˈtʃaːno spalˈletti]; lahir 7 Maret 1959) adalah seorang manajer dan mantan pemain sepak bola dari Italia. Ia saat ini adalah manajer tim nasional Italia.',
          gambar: 'https://i.dailymail.co.uk/i/pix/2017/06/09/15/4148CC9A00000578-0-image-a-28_1497019585960.jpg',
          kategori: 'Pelatih'
        },
        {
          judul: 'Liga Champions UEFA',
          informasi: ' Dalam sejarah Piala/Liga Champions, Inter Milan sudah enam kali masuk ke partai final, termasuk musim ini. Dalam dua kesempatan pertama masuk final, Inter Milan selalu juara: musim 1963-1964 dan 1964-1965. ',
          gambar: 'https://th.bing.com/th/id/OIP.gj4aXZtQOBP-7spPHqO9sAHaHa?rs=1&pid=ImgDetMain',
          kategori: 'tropi'
        },
        {
          judul: 'Tropi Scudeto',
          informasi: 'Inter Milan berhasil meraih Scudetto ke-20 pada musim 2023/2024. Mereka dinobatkan sebagai juara Serie A pada pekan ke-33, tepatnya pada Selasa, 23 April 2024. Kemenangan ini membuat Inter berhak menyematkan dua bintang emas sebagai penghargaan atas prestasi mereka dalam sejarah liga Italia1',
          gambar: 'https://3.bp.blogspot.com/-fHMwPuKA5a4/V1qBkjUMPSI/AAAAAAAAAHI/IXK5NeoAF70Y3pBpbwmfOvATXkcaB2OYgCLcB/s1600/Italy-Serie-A-Cup.jpgg',
          kategori: 'tropi'
        },
        {
          judul: 'SuperCopa Italia',
          informasi: 'Inter Milan menjadi juara Coppa Italia 2022-2023 setelah mengalahkan Fiorentina pada Kamis (25/5/2023) dini hari WIB. Laga Fiorentina vs Inter Milan di final Coppa Italia yang berlangsung di Stadion Olimpico berakhir dengan skor 1-2.',
          gambar: 'https://th.bing.com/th/id/OIP.t090arq1vQ0y-zqmayuf2gHaL_?rs=1&pid=ImgDetMain',
          kategori: 'tropi'
        },
        {
          judul: 'antonio conte',
          informasi: 'Antonio Conte (pelafalan dalam bahasa Italia: [anˈtɔːnjo ˈkonte]; lahir 31 Juli 1969) adalah seorang pelatih sepak bola dan mantan pemain sepak bola profesional asal Italia.',
          gambar: 'https://public.urbanasia.com/images/post/2021/05/26/1622025949-conte.jpg',
          kategori: 'Pelatih'
        },
        {
          judul: 'Jersey kemenangan',
          informasi: 'Seragam peringatan Home Stadium edisi terbatas untuk merayakan perebutan gelar liga ke-20 dan perolehan bintang kedua. Di bagian belakang terdapat personalisasi khusus dengan bintang 2 dan angka 20 berwarna emas',
          gambar: 'src/assets/Screenshot 2024-05-25 001751.jpg',
          kategori: 'Jersey kemenangan'
        },
      ]
    };
  },
  computed: {
    filteredData() {
      return this.items.filter(item => item.kategori === this.currentFilter);
    }
  },
  methods: {
    tampilkanData(judul, informasi) {
      if (this.dataTerpilih && this.dataTerpilih.judul === judul) {
        this.dataTerpilih = null;
      } else {
        this.dataTerpilih = { judul, informasi };
      }
    },
    filterData(kategori) {
      this.currentFilter = kategori;
      this.dataTerpilih = null; // Reset data terpilih ketika mengubah filter
    }
  }
};
</script>

<style>
.buttons {
  display: flex;
  justify-content: center;
  margin-bottom: 20px;
}
.buttons button {
  margin: 0 10px;
  padding: 10px 20px;
  cursor: pointer;
}
.tampilan-data {
  position: fixed;
  bottom: 25px;
  right: 25px; /* Ubah posisi right ke 25px */
  max-width: 300px; /* Sesuaikan lebar maksimum sesuai kebutuhan */
  padding: 10px;
  border: 1px solid #ccc;
  border-radius: 8px;
  background-color: #f9f9f9;
  box-shadow: 0px 4px 6px rgba(0, 0, 0, 0.1);
}
</style>