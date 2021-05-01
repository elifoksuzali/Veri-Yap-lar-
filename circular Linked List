#include<stdio.h>
#include<stdlib.h>
struct node {
  int veri;
  struct node* adres;
};
struct node* ilkEleman;
// eleman ekleme methodunu kuruyoruz
int elemanEkle(int veri1) {
  printf("\n%d Dosyadan listeye eklendi\n", veri1);
  //listede eleman var olup olmadığını kontrol ediyoruz
  if (ilkEleman == NULL) {
    // o adrese bellekten yer ayırtıyoruz.
    ilkEleman = (struct node*)malloc(sizeof(struct node));
    ilkEleman->veri = veri1; //veriyi parametre olarak alıp veri1 atıyoruz.
    ilkEleman->adres = ilkEleman;
  }
  // aksi durum söz konusu olduğunda yani listede eleman var ise
  else {
    struct node* temp1 = ilkEleman;
    struct node* temp2; //yeni bir yer alıyoruz bellekten
    temp2 = (struct node*)malloc(sizeof(struct node)); // yer ayırtıp
    temp2->veri = veri1; // göstereceği adresi adresi veriyoruz.
    temp2->adres = ilkEleman;
    while (temp1->adres != ilkEleman) {
      temp1 = temp1->adres;
    }
    temp1->adres = temp2;// bulana kadar bir sonraki düğüme geç
  }return 0;
}

void elemanSil(int a) {
  int flag = 0; //Silmek istediğimiz eleman yoksa için tutulan değer
  if (ilkEleman->veri == a) { // ilk eleman ise silmek istediğimiz
    struct node* temp1 = ilkEleman; //ilk elemanı boş bir değişkene bağladık
    while (temp1->adres != ilkEleman) { //ilk elemanın adresine gelmedikçe
          temp1 = temp1->adres; //bir sonrakini işaret et   
  }
    struct node* temp = ilkEleman;
    ilkEleman = ilkEleman->adres;//ilk elemanın adresinden sonra devam
    temp1->adres = ilkEleman; // artık ilk elemanın adresi bulundu
    free(temp); //sil
  }
  else if (ilkEleman->veri != a) { //silmek istediğimiz ilk eleman değilse
       struct node* temp1 = ilkEleman;//yeni bir düğüm oluştur
       while (temp1->adres->veri != a && temp1->adres!=ilkEleman) {// bu düğüm adresi verindeki veri silmek istediğimiz değilse ve yeni düğümün adresi ilk eleman değilse
              temp1 = temp1->adres;// bulana kadar bir sonraki düğüme geç
       }
        if(temp1->adres == ilkEleman){ //bulmak istenen o ise
          flag = 1;//silmeyi 1 yap
        }
        else{  
             struct node* temp2 = temp1->adres;// sileceğimizi boşa attık
             {

  temp1->adres = temp1->adres->adres; //silinen adresinin adresinin adresini işaret ettik
              free(temp2); //ve silinecek olanı sildik
               printf("%d elemanı silindi  \n",a);     
             }
        }
  }
  if(flag == 1)// eğer arana öyle eleman yoksa
  {
    printf("\nBöyle bir eleman bulunmamaktadır : %d\n",a);
  }   
}

void listele() // yapılan işlemeleri listelemek için
{
  struct node* temp = ilkEleman; //düğüm oluşturduk
  printf("\nListe\n");
  do 
  { 
    printf("%d listeden okundu \n", temp->veri);//bir sonraki adresi işaret ederek listeleme
    temp = temp->adres;
  } while (temp != ilkEleman); //başa gelemedikçe devam et
}

void başlangıçDeğiştirme(int başlangıçDeğeri , int elemanSayısı) // kullanıcı istediği yerden başlaması için açılan fonksiyon
{
  struct node* temp1 = ilkEleman; //geçici bir düğüm  oluşturuldu
  int değer = 0; //başlanılmak istenen elemanın  listede olup olmadığını kontrol etmek için
  if(başlangıçDeğeri==ilkEleman->veri) //eğer ki başlanmak istenen değer ilk elemansa bu işlemi yap
  {
    listele(); //listele 
  }
  else if (başlangıçDeğeri != ilkEleman->veri) //eğerki başlangıç ilk eleman değilse
  {
    while (temp1->adres != ilkEleman) //eleman üzerinden gezmek için açılan fonksiyon
    {
      temp1 = temp1->adres; //değerin adresini işaret ediyor
      if(temp1->veri == başlangıçDeğeri ) //başlanmak istenen değer o veri ise
      {
        for(int j = 0 ; j <= elemanSayısı-1;j++) //elemanları gez 
        {
          printf("%d\n",temp1->veri); //bulunca ondan gezmeye başla
          temp1 = temp1->adres; //sonrakini işaret eder
          değer = 1; //başlanmak istenen bulunduğunda 1 olur
         
        }
}
      if(değer ==1)  //aynı elemandan iki kere varsa iki kere yazdırmamak için  veya eleman yoksa kontrolü yapmak için
        break;
    }
  }
  if ( değer != 1)
  {
    printf("böyle bir eleman yoktur\n");
    listele();
  }
}

int main() {

  FILE *okunan;
  char ch;
  int y; //dosyadan okunan elemanın atanacağı değişken
  okunan = fopen("kaynak.txt", "r");
  int uzunluk = 0;
  while(1){
    fscanf(okunan,"%d",&y);//okudukça eleman ekle
    elemanEkle(y);
    uzunluk++;//istenilen elemandan başlandıkça artır
    ch = fgetc(okunan);
    if (ch == EOF)//dosyanın sonuna geldiğimizde döngüyü bitirmek için
    {
       break;
    }  
  }      
    fclose(okunan);     //dosya kapat
  int a = 0;
  int b = 0;
  while(b != -1)
  {
    // Kullanıcıya hak tanımak için yapılan işlemler
    printf("\nEleman eklemek için 1 \nSilmek için 2 \nBaşlanmak istenen değer için 3 \nİşlemi bitirmek için -1 giriniz\n");
    scanf("%d" , &b);
    if(b==1)
    {
      printf("Eklemek istediğiniz elemanı giriniz : " );
      scanf("%d" , &a);
      elemanEkle(a);
      listele();
      uzunluk++;
    }
    if(b==2)
    {
      printf("Silmek istediğiniz elemanı giriniz : " );
      scanf("%d" , &a);
      elemanSil(a);
      listele();
      uzunluk--;
    }
    if(b==3)
    {
      printf("Başlatmak istediğiniz elemanı giriniz : " );
      scanf("%d" , &a);
      başlangıçDeğiştirme(a,uzunluk);
    }
  }
  printf("LİSTENİN SON UZUNLUĞU\n %d",uzunluk);
}
