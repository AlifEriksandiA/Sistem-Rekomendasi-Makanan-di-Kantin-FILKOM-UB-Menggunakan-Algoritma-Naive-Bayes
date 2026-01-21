from collections import defaultdict, Counter

# DATA LATIH
data_latih = [
    # MAKANAN TIDAK PEDAS
     ['murah', 'tidak pedas', 'gurih', 'biasa', 'Indomie Goreng'], 
      ['menengah', 'tidak pedas', 'gurih', 'populer', 'Indomie Rendang'],
       ['murah', 'tidak pedas', 'berkuah', 'biasa', 'Mie Sedap Soto'],
        ['murah', 'tidak pedas', 'kering', 'biasa', 'Tahu Telur'],
         ['menengah', 'tidak pedas', 'crispy', 'biasa', 'Ayam crispy'], 
          ['murah', 'tidak pedas', 'berkuah', 'biasa', 'Mie Sedap Ayam Bawang'],
           ['murah', 'tidak pedas', 'kering', 'biasa', 'Nasi Goreng'],
            ['murah', 'tidak pedas', 'berkuah', 'populer', 'Mie Ayam'],
             ['menengah', 'tidak pedas', 'berkuah', 'biasa', 'Mie Ayam Jumbo'],
              ['mahal', 'tidak pedas', 'berkuah', 'biasa', 'Mie Ayam Jumbo + katsu'],
               ['murah', 'tidak pedas', 'gurih', 'populer', 'Mie yamin'],
                ['mahal', 'tidak pedas', 'gurih', 'populer', 'Mie yamin Jumbo + katsu'],
    # MAKANAN SEDANG
     ['murah', 'sedang', 'kering', 'biasa', 'Tahu Telur'],
      ['murah', 'sedang', 'kering', 'biasa', 'Nasi Goreng'],
       ['murah', 'sedang', 'berkuah', 'populer', 'Mie Ayam'],
        ['menengah', 'sedang', 'berkuah', 'biasa', 'Mie Ayam Jumbo'],
         ['mahal', 'sedang', 'berkuah', 'biasa', 'Mie Ayam Jumbo + katsu'], 
          ['murah', 'sedang', 'gurih', 'populer', 'Mie yamin'],
           ['mahal','sedang', 'gurih', 'populer', 'Mie yamin Jumbo + katsu'],
            ['murah', 'sedang', 'gurih', 'populer', 'Mie yamin'],
             ['mahal', 'sedang', 'gurih', 'populer', 'Mie yamin Jumbo + katsu'],
    # MAKANAN PEDAS
     ['murah', 'pedas', 'gurih', 'populer', 'Indomie Ayam Geprek'],
      ['menengah', 'tidak pedas', 'crispy', 'biasa', 'Katsu Ayam'],
       ['menengah', 'pedas', 'kering', 'biasa', 'Nasi Gila'],
        ['mahal', 'pedas', 'kering', 'populer', 'Nasi Gila + katsu'],
         ['murah', 'pedas', 'kering', 'biasa', 'Tahu Telur'],
          ['murah', 'pedas', 'kering', 'biasa', 'Nasi Goreng'],
           ['murah', 'pedas', 'berkuah', 'populer', 'Mie Ayam'],
            ['menengah', 'pedas', 'berkuah', 'biasa', 'Mie Ayam Jumbo'],
             ['mahal', 'pedas', 'berkuah', 'biasa', 'Mie Ayam Jumbo + katsu'],
              ['murah', 'pedas', 'gurih', 'populer', 'Mie yamin'],
               ['mahal', 'pedas', 'gurih', 'populer', 'Mie yamin Jumbo + katsu'],
]

# TRAINING NAIVE BAYES
def train_naive_bayes(data_latih):
    total_data = len(data_latih)
    kelas_counter = Counter([d[4] for d in data_latih])
    fitur_counter = defaultdict(lambda: defaultdict(Counter))  # fitur_counter[fitur][nilai][kelas]

    for budget, selera, karakteristik, populer, makanan in data_latih:
        fitur_counter['budget'][budget][makanan] += 1
        fitur_counter['selera'][selera][makanan] += 1
        fitur_counter['karakteristik'][karakteristik][makanan] += 1
        fitur_counter['popularitas'][populer][makanan] += 1

    return fitur_counter, kelas_counter, total_data

# PREDIKSI
def prediksi_naive_bayes(fitur_counter, kelas_counter, total_data, budget_input, selera_input, karakteristik_input, popularitas_input):
    hasil_prob = {}

    for makanan in kelas_counter:
        prob_makanan = kelas_counter[makanan] / total_data
        prob_budget = (fitur_counter['budget'][budget_input][makanan] + 1) / (kelas_counter[makanan] + 4)
        prob_selera = (fitur_counter['selera'][selera_input][makanan] + 1) / (kelas_counter[makanan] + 4)
        prob_karakteristik = (fitur_counter['karakteristik'][karakteristik_input][makanan] + 1) / (kelas_counter[makanan] + 4)
        prob_popularitas = (fitur_counter['popularitas'][popularitas_input][makanan] + 1) / (kelas_counter[makanan] + 4)

        total_prob = prob_makanan * prob_budget * prob_selera * prob_karakteristik * prob_popularitas
        hasil_prob[makanan] = total_prob

    rekomendasi_teratas = sorted(
        hasil_prob.items(),
        key=lambda x: (x[1], kelas_counter[x[0]]),
        reverse=True
    )[:3]

    return rekomendasi_teratas

# Program utama
if __name__ == "__main__":
  fitur_counter, kelas_counter, total_data = train_naive_bayes(data_latih)
  
  valid_budget = ['murah', 'menengah', 'mahal']
  valid_selera = ['pedas', 'sedang', 'tidak pedas']
  valid_karakteristik = ['crispy', 'gurih', 'berkuah', 'kering']
  valid_popularitas = ['populer', 'biasa']

  nama = input("Nama kamu siapa? ")

  while True:
        budget_input = input("Masukkan budget kamu (murah/menengah/mahal): ").strip().lower()
        if budget_input in valid_budget:
            break
        print("❌ Input tidak valid. Pilihan: murah / menengah / mahal")

  while True:
        selera_input = input("Kamu suka pedas atau tidak pedas? (pedas/sedang/tidak pedas): ").strip().lower()
        if selera_input in valid_selera:
            break
        print("❌ Input tidak valid. Pilihan: pedas / tidak pedas")

  while True:
        karakteristik_input = input("Karakteristik makanan yang kamu suka? (crispy/gurih/berkuah/kering): ").strip().lower()
        if karakteristik_input in valid_karakteristik:
            break
        print("❌ Input tidak valid. Pilihan: crispy / gurih / berkuah / kering")

  while True:
        jawaban_populer = input("Apakah kamu ingin makanan populer? (ya/tidak): ").strip().lower()
        if jawaban_populer in ['ya', 'tidak']:
            popularitas_input = 'populer' if jawaban_populer == 'ya' else 'biasa'
            break
        print("❌ Input tidak valid. Jawab dengan 'ya' atau 'tidak'.")

  hasil = prediksi_naive_bayes(
        fitur_counter,
        kelas_counter,
        total_data,
        budget_input,
        selera_input,
        karakteristik_input,
        popularitas_input
    )

  print(f"\nHalo {nama}, berikut rekomendasi makanan untukmu:")
  for nama_makanan, skor in hasil:
        print(f"- {nama_makanan} (skor probabilitas: {skor:.6f})")

  rekomendasi_utama = hasil[0][0] if hasil else "Tidak ditemukan"
  print(f"\n👉 Rekomendasi utama untuk kamu adalah: {rekomendasi_utama} 🍽")
