--------------------------------------- YANSINIF---------------------------------------------------
public class Merge {

  private int[] dizimiz;
  private int[] geçiciDeğişken;
  private int length;

  public void Sort(int[] alınanDizi)
  {
  this.length = alınanDizi.length;
  this.dizimiz = alınanDizi;
  this.geçiciDeğişken = new int[length];
  bölmeFonksiyonu(0, length - 1);
  }
  private void bölmeFonksiyonu(int sol, int sağ)
  {
    if (sol < sağ)
    {
      int merkez = sol + (sağ - sol) / 2;            //ORTA
      bölmeFonksiyonu(sol, merkez);                  //SOL
      bölmeFonksiyonu(merkez + 1, sağ);              //SAĞ
      birleştirmeFonksiyonu(sol, sağ, merkez);
    }
  }
  private void birleştirmeFonksiyonu(int sol, int sağ, int merkez)
  {
    for (int i = sol; i <= sağ; i++) geçiciDeğişken[i] = dizimiz[i]; 
    int a = sol;                                    
    int b = merkez + 1;                              
    int c = sol; 
    while(a <= merkez && b <= sağ)
    {
      if(geçiciDeğişken[a] <= geçiciDeğişken[b]) 
      {
        dizimiz[c] = geçiciDeğişken[a]; 
        a++; 
      }
      else
      {
        dizimiz[c] = geçiciDeğişken[b]; 
        b++; 
      }
    c++; 
    }
    while(a <= merkez) 
    {
      dizimiz[c] = geçiciDeğişken[a];
      c++;
      a++;
    }
  }
}


-------------------------------------------------- MAİN --------------------------------------------------------------------------------------
import java.util.*;
import java.util.List;
import java.lang.*;
import java.io.*;

class Main {
  public static void main(String[] args) {
    
    Scanner scan = new Scanner(System.in);
    int[] liste = new int[10] ;
    
    for(int i = 0; i < 10 ; i++)
    {
      System.out.print(i+1 +". sayıyı gir: ");
      int girilenSayı ;
      girilenSayı = scan.nextInt();
      liste[i] = (int)girilenSayı;
    }
  

  File f = new File("hello.txt");
  PrintWriter yaz = null;
  
  try
  {
  yaz = new PrintWriter(new FileOutputStream("hello.txt", true));
  
  for(int j = 0; j < 10 ;j++)
  {
    int a = liste[j];
    yaz.print(a+" , ");
  }
  
  yaz.print("\n");
  Merge m = new Merge();
  m.Sort(liste);
  
  for(int c = 0; c < 10 ; c++)
  {
    int b = liste[c];
    yaz.print(b + " , ");
  }

  yaz.print("\n");
  }

  catch(Exception hata)
  {
    System.out.println("Hata !: "+hata.getMessage());
  }
  yaz.close();
  }
}
