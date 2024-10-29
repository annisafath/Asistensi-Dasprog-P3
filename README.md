# Asistensi-Dasprog-P3
## Soal 
Buatlah Kalkulator sederhana yang bisa menjalankan fungsionalitas kabataku (Kali, Bagi, Tambah, Kurang). Namun agar lebih spesial, kalkulator ini juga bisa digunakan untuk mendapatkan faktorial, KPK, FPB, dan atau fungsi matematis lainnya.
### Penjelasan Code 

Definisi Library 
```c
#include <stdio.h>
```
Fungsi Kabataku 
```c
int tambah(int a, int b) {
    return a + b;
}

int kurang(int a, int b) {
    return a - b;
}

int kali(int a, int b) {
    return a * b;
}

float bagi(int a, int b) {
    if (b != 0)
        return (float)a / b;
    else {
        printf("Error: Pembagian dengan nol tidak valid.\n");
        return 0;
    }
}
```
Fungsi Faktorial 
```c
int faktorial(int n) {
    int hasil = 1;
    for (int i = 1; i <= n; i++) {
        hasil *= i;
    }
    return hasil;
}
```
Operasi FPB dan KPK 
```c
int fpb(int a, int b) {
    while (b != 0) {
        int temp = b;
        b = a % b;
        a = temp;
    }
    return a;
}

int kpk(int a, int b) {
    return (a * b) / fpb(a, b);
}
```
Operasi Kalkulator 
```c
int main() {
    int pilihan, a, b;

    printf("Kalkulator Sederhana\n");
    printf("1. Tambah\n2. Kurang\n3. Kali\n4. Bagi\n5. Faktorial\n6. FPB\n7. KPK\n");
    printf("Pilih operasi (1-7): ");
    scanf("%d", &pilihan);

    if (pilihan >= 1 && pilihan <= 4) {
        printf("Masukkan dua angka: ");
        scanf("%d %d", &a, &b);
    } else if (pilihan == 5) {
        printf("Masukkan angka: ");
        scanf("%d", &a);
    } else if (pilihan == 6 || pilihan == 7) {
        printf("Masukkan dua angka: ");
        scanf("%d %d", &a, &b);
    }

    switch (pilihan) {
        case 1:
            printf("Hasil Tambah: %d\n", tambah(a, b));
            break;
        case 2:
            printf("Hasil Kurang: %d\n", kurang(a, b));
            break;
        case 3:
            printf("Hasil Kali: %d\n", kali(a, b));
            break;
        case 4:
            printf("Hasil Bagi: %.2f\n", bagi(a, b));
            break;
        case 5:
            printf("Hasil Faktorial: %d\n", faktorial(a));
            break;
        case 6:
            printf("Hasil FPB: %d\n", fpb(a, b));
            break;
        case 7:
            printf("Hasil KPK: %d\n", kpk(a, b));
            break;
        default:
            printf("Pilihan tidak valid.\n");
            break;
    }

    return 0;
}
```
