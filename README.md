n = int(input("Masukkan jumlah mahasiswa: "))
m = int(input("Masukkan jumlah mata kuliah: "))

mahasiswa = []
for i in range(n):
    nama = input(f"Masukkan nama mahasiswa ke-{i+1}: ")
    mahasiswa.append(nama)

mata_kuliah = []
for i in range(m):
    mata_kuliah.append(input(f"Masukkan nama mata kuliah ke-{i+1}: "))

nilai_ujian = []
for i in range(n):
    nilai_mahasiswa = []
    for j in range(m):
        nilai = int(input(f"Masukkan nilai ujian {mata_kuliah[j]} untuk {mahasiswa[i]}: "))
        nilai_mahasiswa.append(nilai)
    nilai_ujian.append(nilai_mahasiswa)

print("\nTabel Nilai Ujian:")
print("Nama Mahasiswa".ljust(20), end="")
for mata_kuliah_nama in mata_kuliah:
    print(mata_kuliah_nama.ljust(10), end="")
print()

for i in range(n):
    print(mahasiswa[i].ljust(20), end="")
    for nilai in nilai_ujian[i]:
        print(str(nilai).ljust(10), end="")
    print()

for i in range(n):
    total_nilai = 0
    for nilai in nilai_ujian[i]:
        total_nilai += nilai
    rata_rata = total_nilai / m
    print(f"Rata-rata nilai ujian {mahasiswa[i]}: {rata_rata:.2f}")

for j in range(m):
    nilai_tertinggi = -1
    nilai_terendah = 101
    mahasiswa_tertinggi = []
    mahasiswa_terendah = []
    for i in range(n):
        nilai = nilai_ujian[i][j]
        if nilai > nilai_tertinggi:
            nilai_tertinggi = nilai
            mahasiswa_tertinggi = [mahasiswa[i]]
        elif nilai == nilai_tertinggi:
            mahasiswa_tertinggi.append(mahasiswa[i])

        if nilai < nilai_terendah:
            nilai_terendah = nilai
            mahasiswa_terendah = [mahasiswa[i]]
        elif nilai == nilai_terendah:
            mahasiswa_terendah.append(mahasiswa[i])

    print(f"Nilai tertinggi Mata Kuliah {mata_kuliah[j]}: {nilai_tertinggi}, Mahasiswa: {mahasiswa_tertinggi}")
    print(f"Nilai terendah Mata Kuliah {mata_kuliah[j]}: {nilai_terendah}, Mahasiswa: {mahasiswa_terendah}")

