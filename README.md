<div id="header" align="center">
  <img src="https://3coresol.com/wp-content/uploads/2019/02/Logo-APEX-Best-Practice-2.png" width="500"/>
</div>


# INSTALL APEX ORACLE

1. Download Installer & Lakukan Extract semua file

```sh
https://www.oracle.com/id/database/technologies/xe-downloads.html
https://www.oracle.com/tools/downloads/apex-222-downloads.html
https://www.oracle.com/id/java/technologies/downloads/
https://tomcat.apache.org/download-90.cgi
```

2. Buatkan Folder Oracle pada Partition C (C://Oracle), lalu install setup.exe pada folder OracleXE213_Win64, dan arahkan Path ke C://Oracle , tunggu sampai selesai, akan diminta setup Password

3. Buatkan Folder Apex pada Partition C (C://Apex) , Kopi isi folder apex_22.2 kedalam Folder C://Apex 

4. Install Apex 22.  , Buka Cmd as Administrator dan masuk ketikan, lakukan perintah satu2

```sh
  cd\
  cd Apex\apex
  sqlplus /nolog
  conn sys as sysdba
```
*Jika diminta password, kosongkan saja langsung enter

5. Lakukan Setup, lakukan perintah satu2
   
```sh
  show pdbs;
  alter session set container = XEPDB1;
  COLUMN default_tablespace FORMAT A15
  COLUMN temporary_tablespace FORMAT A15
  @apexins.sql SYSAUX SYSAUX TEMP /i/

  @apex_rest_config.sql ->masukin password
  @apxchpwd.sql

  ALTER USER APEX_PUBLIC_USER ACCOUNT UNLOCK;
  ALTER USER APEX_LISTENER ACCOUNT UNLOCK;
  ALTER USER APEX_REST_PUBLIC_USER ACCOUNT UNLOCK;

  alter pluggable database pdb$seed close;
  alter pluggable database pdb$seed open read write;

```

6. Install ORDS, Buat Folder C://App/ords, masukan isi pada folder installer ORDS, dan buat folder C://App/config/ords/logs
```sh
  cd App/ords
  java -jar ords.war --config C:\App\config install
```
   

