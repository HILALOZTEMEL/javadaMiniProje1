# javadaMiniProje1
//Basit atm kodu

import java.util.Scanner;


public class Main {

    private static String cevap2;//birden çok fonksiyonlarda kullandığım için global tanımladım
    private static String PAdSoyad;


    public static void main(String[] args) {
        Scanner scanner=new Scanner(System.in);
        MusteriTanımlama musteriTanımlama=new MusteriTanımlama();
        do{ //do-while kullandım çünkü isim soy isim doğru ise sisteme girebilir.
            System.out.println("Adızı ve Soyadınız giriniz :..");
            musteriTanımlama.setAdSoyisim(scanner.nextLine());
            PAdSoyad= musteriTanımlama.getAdSoyisim();
            System.out.println("Parolanızı giriniz :..");
            musteriTanımlama.setSifre(scanner.nextLine());

        }while(musteriTanımlama.bilgileriKontrolet()!=1);

        if (musteriTanımlama.bilgileriKontrolet()==1){

            System.out.println("\n Hoşgeldiniz "+PAdSoyad+"....\n");

            int cevap;
            do{//do while çünkü işlemin tekrarlama olasılığı var.
            System.out.println("Yapmak istediğiniz işlemi seçiniz  :\n--->1)hesaptaki parayı sorgulama" +
                    "\n" +
                    "--->2)para yatırma\n" +
                    "--->3)para çekme\n" +
                    "--->4)para gönderme"+"\n" +
                    "--->5)çıkış");
            cevap=scanner.nextInt();

            switch (cevap){
                case 1: hesaptakiparayisorgulama();break;

                case 2: parayatirma();break;

                case 3: paracekme();break;

                case 4: paragonderme();break;

                case 5: break;
                default:
                    System.out.println("Böyle bir seçim yoktur....");

            }
            }while(cevap2.equalsIgnoreCase("e") && cevap!=5);
        }

    }
     public static void hesaptakiparayisorgulama(){
         Scanner scanner=new Scanner(System.in);
         MusteriTanımlama musteriTanımlama=new MusteriTanımlama();
         musteriTanımlama.hesaptakiParaSorgulama(PAdSoyad);
         islemTekrari();


     }

     public static void parayatirma(){
         Scanner scanner=new Scanner(System.in);
         MusteriTanımlama musteriTanımlama=new MusteriTanımlama();
         double yatirilicakParaMiktari;
         do {
             musteriTanımlama.hesaptakiParaSorgulama(PAdSoyad);
             System.out.println("yatırmak istediğiniz para miktarını giriniz  :...");
             yatirilicakParaMiktari= scanner.nextDouble();

             if (yatirilicakParaMiktari>0){
                 musteriTanımlama.hesabaParaYatırma(yatirilicakParaMiktari,PAdSoyad);


             }else{
                 System.out.println("****'-' değer girdiniz...");

             }
             islemTekrari();
         }while (yatirilicakParaMiktari<0);


     }
     public static void paracekme(){
         Scanner scanner=new Scanner(System.in);
         MusteriTanımlama musteriTanımlama=new MusteriTanımlama();
         double cekilecekParaMiktari;
         do {
             musteriTanımlama.hesaptakiParaSorgulama(PAdSoyad);
             System.out.println("çekmek istediğiniz para miktarını giriniz  :...");
             cekilecekParaMiktari= scanner.nextDouble();
             if(cekilecekParaMiktari>0){
                 musteriTanımlama.hesaptanParaDusme(cekilecekParaMiktari,PAdSoyad);


             }else{
                 System.out.println("****'-' değer girdiniz...");

             }

             islemTekrari();

         }while (cekilecekParaMiktari<0);


     }


     public static void paragonderme(){
        Scanner scanner=new Scanner(System.in);
        MusteriTanımlama musteriTanımlama=new MusteriTanımlama();
         String adSoyad;
        do{
            System.out.println("Para göndermek istediğiniz kişinin adı-soyadını giriniz  :..");
            adSoyad=scanner.nextLine();

            if (musteriTanımlama.paraGondermeİcinBilgiKontrolu(adSoyad)==1){
                musteriTanımlama.hesaptakiParaSorgulama(PAdSoyad);
                System.out.println("Göndermek istediğiniz para miktarını giriniz  :.. ");
                double GonderilecekParaMiktari=scanner.nextDouble();//gönderilmek istenen miktar alındı.

                if(GonderilecekParaMiktari>0){
                    if(musteriTanımlama.hesaptanParaDusme(GonderilecekParaMiktari,PAdSoyad)==1) {
                        musteriTanımlama.hesabaParaYatırma(GonderilecekParaMiktari, adSoyad);/*para yatırılamak istenilen kişinin para miktarı
             musteriTanımlama adlı classtaki para yatımak için olan fonksiyona gönderildi.*/
                    }


                }else{
                    System.out.println("****'-' değer girdiniz...");
                }


            }
            islemTekrari();
        }while(musteriTanımlama.paraGondermeİcinBilgiKontrolu(adSoyad)!=1);



     }
     public static void islemTekrari(){
         Scanner scanner=new Scanner(System.in);
         System.out.println("yapmak istediğiniz başka bir işlem var mı? (e/h)   ");
         cevap2 =scanner.nextLine();
         while(!(cevap2.equalsIgnoreCase("e"))&&!(cevap2.equalsIgnoreCase("h")))
          {

                  System.out.println("!!!hatalı seçim yaptınız...!!!");
                  System.out.println("yapmak istediğiniz başka bir işlem var mı? (e/h)   ");
                  cevap2 =scanner.nextLine();

          }
     }



}



--------------------------



public class MusteriTanımlama{

    private String AdSoyisim;
    private String sifre;

    public String getAdSoyisim() {
        return AdSoyisim;
    }

    public void setAdSoyisim(String adSoyisim) {
        AdSoyisim = adSoyisim;
    }

    public String getSifre() {
        return sifre;
    }

    public void setSifre(String sifre) {
        this.sifre = sifre;
    }

    String[] isimSoyisim={"hilal öztemel","sude kaya","ahmet aksoy","sedef yazıcı","betül ucar"};
    String[] parola={"Hill5245","su45de","12345","se85563","bet5686"};
    private  static double[] hesapParaMiktari={100000,20000,30000,62225,85647};


    public int bilgileriKontrolet(){
        int k=0;//k dizide bulunamama durumunu temsil eder
        for(int i=0;i< isimSoyisim.length;i++){
            if (getAdSoyisim().equals(isimSoyisim[i])&&getSifre().equals(parola[i])){

                return 1;
            }else{

                k++;
                if (k==isimSoyisim.length){//k dizide bulunamama durumunu temsil eder
                    System.out.println("isim soyyisim yada sifre yanlıs");
                }


            }

        }
        return 0;

    }



    public int paraGondermeİcinBilgiKontrolu(String musterismi){
        int k=0;//k=böyle bir müşterinin bulunmama surumunu temsil eder.
        for(int i=0;i< isimSoyisim.length;i++){
            if (musterismi.equals(isimSoyisim[i])){

                return 1;

            }else{

                k++;
                if (k== isimSoyisim.length){//k=böyle bir müşterinin bulunmama surumunu temsil eder.
                    System.out.println("Böyle bir müşteri bulunamamaktadır...");
                }

            }



        }
        return 0;
    }


    /*private  static double paraMik;//arrayin içinde toplam parayı yerelde azaltabiliyorum ama globalde azalmıyor. bu da globalde azaltmak için
    private  static int k=0;//globalde dizininin idexini belirlemek için*/

    public double hesabaParaYatırma(double paraMiktari, String adSoyad){/*bir başkasının hesabına para yatırma*/

        for (int i=0;i< isimSoyisim.length;i++){
            if (adSoyad.equals(isimSoyisim[i])){

                hesapParaMiktari[i]+=paraMiktari;
                System.out.println(isimSoyisim[i]+" kişisinin hesabına Para yatırma işlemi gerçekleşmiştir.");

                System.out.println("----->Test Amaçlı:");//para yatırılan kişi hesabına yatılan para yı test amaçlı kontrol ettim.
                System.out.println("----->"+isimSoyisim[i]+" kişisinin hesabındaki para miktarı : "+hesapParaMiktari[i]);
            }
        }



        return 0;
    }




    public int hesaptanParaDusme(double paraMiktari,String adSoyad){
        for (int i=0;i< isimSoyisim.length;i++){
            if (adSoyad.equals(isimSoyisim[i])){

                    if (hesapParaMiktari[i]>paraMiktari){
                        hesapParaMiktari[i]=hesapParaMiktari[i]-paraMiktari;

                        System.out.println(isimSoyisim[i]+" Hesabınızda kalan para miktarı  = "+hesapParaMiktari[i]);
                        return 1;

                    }else{
                        System.out.println("hesabınızda bu kadar para bulunamaktadır.");

                    }



            }
        }
       return 0;
    }

    public  double hesaptakiParaSorgulama(String adSoyad){

        for (int i=0;i< isimSoyisim.length;i++){
            if (adSoyad.equals(isimSoyisim[i])){

                System.out.println("Hesabınızdaki para miktarı : "+hesapParaMiktari[i]+ " tl dir");
            }
        }

        return 0;
    }


}

