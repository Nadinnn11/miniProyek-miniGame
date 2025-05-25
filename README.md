//# miniProyek-minigame/
#include <stdio.h>
#include <stdlib.h>


int usia, energi;
 
void setEnergi() //setEnergi digunakan untuk perolehan energi yang bisa dimiliki setiap user sesuai dengan usianya/
{
    if(usia >= 10 && usia <= 20){  //semakin tua usia user, maka semakin kecil energi yang dimilikinya/
        energi = 600;
    }
    else if(usia >= 21 && usia <= 30){
        energi = 500;
    }
    else if(usia >= 31 && usia <= 40){
        energi = 400;
    }
    else if(usia >= 41 && usia <= 50){
        energi = 300;
    }
    else {
        energi = 200;
    }
}

void diamond() //diamond merupakan hadiah yang diterima oleh user apabila mengambil keputusan yang tepat/
{
    int n = 5;
    for (int i = 0; i < n; i++) {
        for (int j = 0; j < n - i - 1; j++) {
            printf(" ");
        }
        int k = 0; 
        while(k < 2 * i + 1) {
            printf("*");
            k++;
        }
        printf("\n");
    }
    for (int i = n - 2; i >= 0; i--) {
        for (int j = 0; j < n - i - 1; j++) {
            printf(" ");
        }
        int k = 0;
        while(k < 2 * i + 1) {
            printf("*");
            k++;
        }
        printf("\n");
    
    }
}

void tidakBeruntung() //tidak beruntung merupakan posisi dimana user mengambil keputusan yang merugikan dirinya/
{
    int n = 45;
    for (int i = 0; i <= n; i++ ) {
        printf("==");
    }
    printf("\n                            -SELAMAT JALAN-\n");
    printf("keputusan hidup menentukan masa depanmu, pertimbangkan semuanya sebaik mungkin!\n");
    for (int i = 0; i <= n; i++ ) {
        printf("=="); 
    }
    printf("\n");
    
}



int main()
{
    int start = 1;
    int pilihan;
    int alur = 0; 

    int n = 45;
    for (int i = 0; i <= n; i++ ) {
        printf("==");
    }
    printf("\n                                --SELAMAT DATANG DI DUNIA ENTERNIA--\n");
    for (int i = 0; i <= n; i++ ) {
        printf("==");
    }

    printf("\n**silahkan klik 1 untuk melanjutkan petualangan**\n");
    scanf("%d", &start);

  //program akan meminta input usia kemudian melakukan pengecekan batas usia/
    do {
        printf("\n**Berapa usiamu saat ini? (10-100)**\n");
        scanf("%d", &usia);
        if(usia < 10 || usia > 100) {
            printf("Usia harus antara 10 sampai 100 tahun!\n");
        }
    } while(usia < 10 || usia > 100);

    setEnergi();
    printf("Energi kamu: %d\n", energi);

    while(start) {
        int alurSebelumnya = alur; //apabila user memberikan input diluar pilihan yang diberikan, maka program akan memulai kembali ke alur sebelumnya
        /*setiap alur memiliki pilihan masing-masing
         * beberapa pilihan cerita memiliki alur yang sama karena keputusan yang diambil telah disetting memiliki nilai keberanian atau tidak
         * semakin berani user mengambil keputusan, maka energi yang dia dapat akan bertambah dan jalan yang ditempuh semakin mudah*/
        if(alur == 0) {
            printf("\n====PETUALANGAN DI DUNIA ENTERNIA====\n");
            printf("Kamu tersesat sendirian di hutan yang gelap dan di hadapanmu ada sebuah gua misterius, apa yang akan kamu lakukan untuk pertama kali?\n");
            printf("**masukkan angka untuk melanjutkan pilihan**\n");
            printf("Pilih jalan hidupmu:\n");
            printf("1. masuk kedalam gua\n"); 
            printf("2. mencari jalan lain menuju kerajaan enternia\n");
            printf("3. berdiam diri\n");
            
            scanf("%d", &pilihan);

            //opsi awal dari cerita/
            if(pilihan == 1) { 
                alur = 1;              
                energi -= 100;
                
            } 
            else if(pilihan == 2) {
                alur = 2; 
            } 
            else if(pilihan == 3) {
                alur = 3; 
            } 
            else {
                printf("Silahkan masukkan angka agar pilihan anda valid, pilih angka 1 sampai 3!\n");
                alur = alurSebelumnya;
            }
        }
        else if(alur == 1){ //alur cerita 1/
            printf("**saat memasuki gua, hujan mulai turun dan kamu terjebak di dalam gua**\n");
            printf("1. kamu meratapi nasib dan menyalahkan takdir\n");
            printf("2. kamu mencari makanan karena mulai lapar\n");
            printf("3. kamu tidur sejenak untuk memulihkan energi\n");

            scanf("%d", &pilihan);

            if(pilihan == 1) { //jika user memberikan pilihan 1, maka user akan langsung dialihkan ke alur cerita 3/
                alur = 3;              
                energi -= 400;
               
            } 
            else if(pilihan == 2) { //jika user memberikan pilihan 2, maka user akan langsung dialihkan ke alur cerita 2/
                alur = 4; 
                energi += 50;
            } 
            else if(pilihan == 3) { //jika user memberikan pilihan 3, maka user akan langsung dialihkan ke alur cerita 4/
                alur = 4; 
                energi += 100;
            } 
            else {
                printf("Silahkan masukkan angka agar pilihan anda valid, pilih angka 1 sampai 3!\n");
                alur = alurSebelumnya;
            }
        }
        else if(alur == 2){ //alur cerita 2/
            printf("**setelah berjalan cukup jauh akhirnya kamu menemukan sungai**\n");
            printf("1. istirahat sejenak dan menyegarkan diri di sungai itu\n");
            printf("2. menyusuri sungai untuk menemukan pedesaan dan mencari tahu jalan menuju kerajaan\n");
            scanf("%d", &pilihan);

            if(pilihan == 1) { //jika user memberikan pilihan 1, maka user akan langsung dialihkan ke alur cerita 5/
                alur = 5;              
                energi += 100;
                printf("Energi kamu bertambah\n");
            } 
            else if(pilihan == 2) { //jika user memberikan pilihan 2, maka user akan langsung dialihkan ke alur cerita 6/
                alur = 6; 
                energi -= 50;
            } 
            else {
                printf("Silahkan masukkan angka agar pilihan anda valid, pilih angka 1 atau 2!\n");
                alur = alurSebelumnya;
            }
        }
        else if(alur == 3){ 
            printf("Berdiam diri dan pasrah pada keadaan tidak akan menyelesaikan masalahmu, pilih keputusan dari sekarang!\n"); //pesan untuk user agar dapat mengambil keputusan untuk hidupnya sendiri/
            printf("1. mencari makanan atau tidur untuk memulihkan energi\n");
            printf("2. mencari sungai untuk mencari jalan pulang\n");
           
            scanf("%d", &pilihan);

            if(pilihan == 1) { //jika user memberikan pilihan 1, maka user akan langsung dialihkan ke alur cerita 4/
            
                alur = 4;              
                energi -= 200;
                
            } 
            else if(pilihan == 2) { //jika user memberikan pilihan 2, maka user akan langsung dialihkan ke alur cerita 2/
                alur = 2; 
                printf("HEBAT! kamu mulai berani mengambil langkah\n");
            }
            else {
                printf("Silahkan masukkan angka agar pilihan anda valid, pilih angka 1 atau 2!\n");
               
            }
        }
        else if(alur == 4){ //alur cerita 4/
            printf("**Energimu bertambah, apa kamu sudah siap menuju kerajaan?**\n");
            printf("1. ya! aku akan mencari sungai untuk dijadikan sebagai navigator\n");
            printf("2. tidak, lebih baik aku diam dan menunggu bantuan datang\n");
           
            scanf("%d", &pilihan);

            if(pilihan == 1) { //jika user memberikan pilihan 1, maka user akan langsung dialihkan ke alur cerita 2/
                alur = 2;              
            } 
            else if(pilihan == 2) { //jika user memberikan pilihan 2, maka user dinyatakan tidak beruntung/
               tidakBeruntung(); //program akan langsung menampilkan isi dari void tidak beruntung/
             
            } 
            else {
                printf("Silahkan masukkan angka agar pilihan anda valid, pilih angka 1 atau 2!\n");
                alur = alurSebelumnya;
            }
        }
        else if(alur == 5){ //alur cerita 5/
            printf("**kamu sudah siap untuk menyusuri sungai**\n");
            printf("1. aku siap menuju kerajaan!\n");
            printf("2. tidak, aku akan bersantai\n");
           
            scanf("%d", &pilihan);

            if(pilihan == 1) { //jika user memberikan pilihan 1, maka user akan langsung dialihkan ke alur cerita 6/
                alur = 6; 
                energi += 50;             
            } 
            else if(pilihan == 2) { //jika user memberikan pilihan 2, maka energi user akan berkurang sebanyak 500
                energi -= 500; 
            } 
            else {
                printf("Silahkan masukkan angka agar pilihan anda valid, pilih angka 1 atau 2!\n");
                alur = alurSebelumnya;
            }
        }
        else if(alur == 6){ //alur ceerita 6 dan output yang diterima oleh user apabila mengambil keputusan yang tepat/
            printf("**setelah menyusuri sungai yang begitu panjang akhirnya kamu menemukan kerajaan**\n");
            printf("Disana kamu mendapatkan hadiah dari raja karena kamu adalah orang asing pertama yang berhasil memasuki kerajaan enternia\n");
            for (int i = 0; i <= n; i++ ) {
                printf("==");   
            }
            printf("\n``inilah hadiah yang kamu dapat``\n");
            diamond();
            for (int i = 0; i <= n; i++ ) {
                printf("==");
            }
            printf("\nsisa energi kamu : %d\n", energi);
            printf("SELAMAT! Kamu berhasil menyelesaikan petualangan!\n");
            return 0;
            
        }
        
        if(energi > 0 && energi < 100){ //jika energi yang dimiliki user ada di rentan 1-99 maka user dinyatakan tidak beruntung(sekarat)/
            tidakBeruntung();
        }
        
        if(energi <= 0){
            printf("\nKamu mati dalam game ini...\n");//apabila energi yang dimiliki user kurang dari 0, maka user mati dalam game ini/
            printf("Terlalu banyak keraguan dalam dirimu, mulai ambil keputusan sebagai langkah kecil untuk masa depanmu, hidupmu ada ditanganmu!\n");
          return 0;
        }
    }

    return 0; //program mengembalikan ke nilai awal/
}
