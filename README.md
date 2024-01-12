# UAS-PEMOGRAMAN-VISUAL

.

https://youtu.be/PLpnJzle7RU?si=A-f0hMB8V4aflZaG

.

![FOTO UAS PM](https://github.com/ManurungAlexR/UAS-PEMOGRAMAN-VISUAL/assets/101391579/98f1de7b-b17c-4354-9471-7e28c7d4869e)

.
ini kode untuk data makanan
.

unit UAS1;

{$mode objfpc}{$H+}

interface

uses
  Classes, SysUtils, odbcconn, SQLDB, DB, Forms, Controls, Graphics, Dialogs,
  DBCtrls, DBGrids, StdCtrls;

type

  { TForm1 }

  TForm1 = class(TForm)
    btnkeluar: TButton;
    btntambah: TButton;
    btnedit: TButton;
    btnhapus: TButton;
    DataSource1: TDataSource;
    DBEnama: TDBEdit;
    DBEharga: TDBEdit;
    DBEkategori: TDBEdit;
    DBEstok: TDBEdit;
    DBEsatuan: TDBEdit;
    DBGrid1: TDBGrid;
    DBNavigator1: TDBNavigator;
    Label1: TLabel;
    Label2: TLabel;
    Label3: TLabel;
    Label4: TLabel;
    Label5: TLabel;
    Label6: TLabel;
    ODBCConnection1: TODBCConnection;
    SQLQuery1: TSQLQuery;
    SQLTransaction1: TSQLTransaction;
    procedure btneditClick(Sender: TObject);
    procedure btnhapusClick(Sender: TObject);
    procedure btnkeluarClick(Sender: TObject);
    procedure btntambahClick(Sender: TObject);
    procedure DBEnamaChange(Sender: TObject);
    procedure FormCreate(Sender: TObject);
  private

  public

  end;

var
  Form1: TForm1;

implementation

{$R *.lfm}

{ TForm1 }

procedure TForm1.FormCreate(Sender: TObject);
begin

end;

procedure TForm1.btnkeluarClick(Sender: TObject);
begin
  if MessageDlg('perhatian','Apakah anda ingin keluar?', mtConfirmation,[mbYes,mbNo],0)= mrYes then
   Application.Terminate;
end;

procedure TForm1.btneditClick(Sender: TObject);
begin
  if SQLQuery1.RecordCount>0 then
  begin
    if btntambah.Caption='tambah' then
    begin
      SQlQuery1.Edit;
      btnedit.Caption:='simpan';
      exit
   end
   else
   begin
    if(DBEnama.Text= '')or(DBEkategori.Text= '')or(DBEsatuan.Text= '')or(DBEharga.Text= '')or(DBEstok.Text='') then
    SQLQuery1.post;
    SQLQuery1.ApplyUpdates;
    btnedit.Caption:='edit';
    MessageDlg('sukses','berhasil melakukan perubahan data baru',mtinformation, [mbOK],0);
   end;
 end;
end;

procedure TForm1.btnhapusClick(Sender: TObject);
begin
  if MessageDlg('perhatian','Apakah anda ingin menghapus?', mtConfirmation,[mbYes,mbNo],0)= mrYes then
   Application.Terminate;
end;

procedure TForm1.btntambahClick(Sender: TObject);
begin
  if btntambah.Caption='tambah' then
  begin
   SQLQuery1.insert;
   btntambah.Caption:='simpan';
   MessageDlg('sukses','berhasil menyimpan data baru',mtinformation, [mbOK], 0);
   end
end;

procedure TForm1.DBEnamaChange(Sender: TObject);
begin

end;

end.
