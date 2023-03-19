
impor  jawa . menggunakan . ArrayList ;
impor  jawa . menggunakan . HashMap ;
impor  jawa . menggunakan . Pemindai ;

 tugas2 kelas  umum {
  public  static  void  main ( String [] args ){
     Pemindai pemindai = Pemindai baru  ( Sistem .in ) ;

    String [][] Buah = {
      { "apel" , "35000" },
      { "jeruk" , "50000" },
      { "mangga" , "25000" },
      { "duku" , "15000" },
      { "semangka" , "20000" },
    };
    ArrayList < String []> keranjangBuah = new  ArrayList < String []>();

    int  pilihan ;

    sementara ( benar ) {
      Sistem . keluar . println ( "Menu:" );
      Sistem . keluar . println ( "1. Beli buah" );
      Sistem . keluar . println ( "2.Struk belanja" );
      Sistem . keluar . println ( "3.Keluar" );

      Sistem . keluar . print ( "Masukan pilihan: " );
      pilihan = pemindai . nextInt ();

      jika ( pilihan == 3 ){
        istirahat ;
      }

      jika ( pilihan == 1 ){

        printTable ( new  String [] { "Buah" , "Harga" }, Buah );
        Sistem . keluar . print ( "Pilih buah (0-4): " );
        int  indexBuah = scanner . nextInt ();
        Sistem . keluar . print ( "Masukan jumlah: " );
        int  jumlah = pemindai . nextInt ();

        coba {
          String [] buah = Buah [ indexBuah ];

          for ( int  i = 0 ; i < jumlah ; i ++){
            keranjangBuah . tambah ( buah );
          }
        } tangkap ( Pengecualian  e ) {
          Sistem . keluar . println ( "Buah tidak tersedia" );
        }
      }

      jika ( pilihan == 2 ){
        HashMap < String [], String []> daftarBelanjaan = new  HashMap <>();

        for ( int  i = 0 ; i < keranjangBuah . size (); i ++){
          String [] belanjaan = daftarBelanjaan . get ( keranjangBuah . get ( i ));
          if ( belanjaan == null ){
            belanjaan = String baru  [] {
              keranjangBuah . dapatkan ( i ) [ 0 ],
              "0" ,
              keranjangBuah . dapatkan ( i ) [ 1 ],
              "0"
            };
          }

          belanjaan [ 1 ] = Bilangan Bulat . toString ( Integer .parseInt ( belanjaan [ 1 ]) + 1 ) ;
          belanjaan [ 3 ] = Bilangan Bulat . toString ( Integer .parseInt ( belanjaan [ 1 ]) * Integer .parseInt ( belanjaan [ 2 ]) ) ;
          daftarBelanjaan . put ( keranjangBuah . get ( i ), belanjaan );
        }

        printTable ( new  String [] { "Nama buah" , "Jumlah" , "Harga" , "Subtotal" }, daftarBelanjaan .values ​​( ) .toArray ( new  String [ daftarBelanjaan .size ( )][ 4 ]));
      }
    }
    pemindai . tutup ();
  }

  static  void  printTable ( String [] kolom , String [][] data ){

    Sistem . keluar . println ( "\n========================================== ===================================" );
    Sistem . keluar . print ( "No.\t" );
    untuk ( int  i = 0 ; i < kolom .panjang ; i ++) {
      Sistem . keluar . cetak ( kolom [ i ]);
      jika ( kolom [ i ]. panjang () >= 8 ){
        Sistem . keluar . cetak ( "\t" );
      } lain {
        Sistem . keluar . cetak ( "\t\t" );
      }
    }

    Sistem . keluar . println ();
    untuk ( int  i = 0 ; i < data .panjang ; i ++) {
      Sistem . keluar . cetak ( i ​​+ 1 + "\t" );
      untuk ( int  j = 0 ; j < kolom .panjang ; j ++) {
        Sistem . keluar . cetak ( data [ i ][ j ]);
        jika ( data [ i ][ j ]. panjang () >= 8 ){
          Sistem . keluar . cetak ( "\t" );
        } lain {
          Sistem . keluar . cetak ( "\t\t" );
        }
      }
      jika ( i == data .panjang - 1 ) {
        Sistem . keluar . println ( "\n========================================== ===================================" );
      } lain {
        Sistem . keluar . println ();
      }
    }
  }
}
