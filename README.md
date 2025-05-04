def bandingkan_file(nama_file1, nama_file2):
    """
    Membandingkan dua file teks baris demi baris dan menampilkan perbedaannya.

    Args:
        nama_file1 (str): Nama file teks pertama.
        nama_file2 (str): Nama file teks kedua.
    """
    try:
        with open(nama_file1, 'r') as file1, open(nama_file2, 'r') as file2:
            baris1 = file1.readline()
            baris2 = file2.readline()
            nomor_baris = 1
            perbedaan_ditemukan = False

            while baris1 != '' or baris2 != '':
                baris1_strip = baris1.strip()
                baris2_strip = baris2.strip()

                if baris1_strip != baris2_strip:
                    print(f"Perbedaan pada baris ke-{nomor_baris}:")
                    if baris1 != '':
                        print(f"  File 1: {baris1_strip}")
                    if baris2 != '':
                        print(f"  File 2: {baris2_strip}")
                    perbedaan_ditemukan = True

                baris1 = file1.readline()
                baris2 = file2.readline()
                nomor_baris += 1

            if not perbedaan_ditemukan:
                print("Kedua file identik.")

    except FileNotFoundError:
        print("Salah satu atau kedua file tidak ditemukan.")
    except Exception as e:
        print(f"Terjadi kesalahan: {e}")

# Contoh penggunaan
nama_file_1 = "file1.txt"
nama_file_2 = "file2.txt"

# Membuat contoh isi file (untuk demonstrasi)
with open(nama_file_1, 'w') as f:
    f.write("Ini adalah baris pertama dari file 1.\n")
    f.write("Baris kedua file 1 berbeda.\n")
    f.write("Ini baris ketiga di file 1.\n")
    f.write("Baris keempat.\n")

with open(nama_file_2, 'w') as f:
    f.write("Ini adalah baris pertama dari file 2.\n")
    f.write("Baris kedua file 2 ini beda.\n")
    f.write("Ini baris ketiga di file 1.\n")
    f.write("Baris kelima.\n")

bandingkan_file(nama_file_1, nama_file_2)
