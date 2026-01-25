Example of code, that was generated and written by me with the help of AI.

First working state of the code:

```pas
procedure TForm1.Button1Click(Sender: TObject);
begin
  IBQuery1.Database := IBDatabase1;
  IBQuery1.Transaction := IBTransaction1;
  IBQuery1.Transaction.DefaultDatabase := IBDatabase1;
  IBQuery1.SQL.Text :=
    'SELECT SIFZDR, NAZZDR FROM ZDRAVNIKI WHERE POLNINAZIV IS NOT NULL AND TRIM(POLNINAZIV) <> '''';';

  DataSource1.DataSet := IBQuery1;

  Zdravniki.DataSource := DataSource1;
  Zdravniki.UserName := 'Zdravniki';

  if not IBDatabase1.Connected then
    IBDatabase1.Connected := True;

  if not IBTransaction1.Active then
    IBTransaction1.StartTransaction;

  if not IBQuery1.Active then
    IBQuery1.Open;


  frxReport1.ShowReport();
end;
```

Final code:

```pas
procedure TForm1.Button1Click(Sender: TObject);
begin
  IBQuery1.Database := IBDatabase1;
  IBQuery1.SQL.Text :=
    'SELECT SIFZDR, NAZZDR, POLNINAZIV FROM ZDRAVNIKI WHERE TRIM(POLNINAZIV) <> '''';';

  DataSource1.DataSet := IBQuery1;

  Zdravniki.DataSource := DataSource1;
  Zdravniki.UserName := 'Zdravniki';

  frxReport1.ShowReport();
end;
```
