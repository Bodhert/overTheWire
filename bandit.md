0. level - 0
```console
$ ssh bandit0@bandit.labs.overthewire.org -p 2220
$ cat readme
// boJ9jbbUNNfktd78OOpsqOltutMc3MY1 what cotains my readme 
```

1. level - 1
```console
$ ssh bandit1@bandit.labs.overthewire.org -p 2220
// paswd boJ9jbbUNNfktd78OOpsqOltutMc3MY1
$ cat ./-
// CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
```


2. level 2
```console
$ ssh bandit2@bandit.labs.overthewire.org -p 2220
// paswd CV1DtqXWVFXTvM2F0k09SHz0YwRINYA9
$ cat spaces\ in\ this\ filename 
// UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
```

3. level 3
```console
$ssh bandit3@bandit.labs.overthewire.org -p 2220
//passwd UmHadQclWmgdLOKQ3YNgjWxGoRMb5luK
$cat inhere/.hidden 
//pIwrPrtPN36QITSp3EQaw936yaFoFgAB
```

4. level 4
```console
$ ssh bandit4@bandit.labs.overthewire.org -p 2220
// passwd pIwrPrtPN36QITSp3EQaw936yaFoFgAB
$ cat ./-file07
// koReBOKuIDDepwhWk7jZC0RTdopnAYKh
```

5. level 5
```console
$ ssh bandit5@bandit.labs.overthewire.org -p 2220
// passwd koReBOKuIDDepwhWk7jZC0RTdopnAYKh
$ ~/inhere find . -size 1033c -type f -exec grep -Iq . {} \; -and -print 

//DXjZPULLxYr17uwoI01bNLQbtFemEgo7
```
[help 1](http://www.ducea.com/2008/02/12/linux-tips-find-all-files-of-a-particular-size/)

[help 2](https://unix.stackexchange.com/questions/313442/find-human-readable-files)

[help 3](https://stackoverflow.com/questions/4767396/linux-command-how-to-find-only-text-files)

[help 4](https://stackoverflow.com/questions/22122643/how-to-check-if-a-regular-file-is-executable-or-not-in-linux
)



6. level 6
```console
$ ssh bandit6@bandit.labs.overthewire.org -p 2220
// paswd: DXjZPULLxYr17uwoI01bNLQbtFemEgo7
$ find /  -group bandit6 -user bandit7 -size 33c
// then I realize (trough reading the permisions) that the only file accecible with was in /var/lib/dpkg/info/bandit7.password
$ cat /var/lib/dpkg/info/bandit7.password
// yields HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
```

7. level 7
```console
$ ssh bandit7@bandit.labs.overthewire.org -p 2220
// passwd : HKBPTKQnIay4Fw76bEy8PVxKEDQRKTzs
$ cat data.txt | grep millionth
  millionth	cvX2JJa4CFALtqS87jk27qwqGhBM9plV
```

8. level 8 
```console
$ ssh bandit8@bandit.labs.overthewire.org -p 2220
// paswd cvX2JJa4CFALtqS87jk27qwqGhBM9plV
$ cat data.txt | sort | uniq -u
 UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
```

9. level 9
```console
$ ssh bandit9@bandit.labs.overthewire.org -p 2220
// paswd UsvVyFSfZZWbi6wgC7dAFyFuR6jQQUhR
$ xxd data.txt
//  truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk seaching by eye, i found it
// beter soution strings data.txt | grep =
```

10. level 10
```console
$ ssh bandit10@bandit.labs.overthewire.org -p 2220
// truKLdjsbJ5g7yyJ2X2R0o3a5HQJFuLk
$ base64 -d data.txt
The password is IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
```

11. level 11
```console
$ ssh bandit11@bandit.labs.overthewire.org -p 2220
// IFukwKGsFW8MOq3IRFqrxE1hxTNEbUPR
$ cat data.txt | tr 'A-Za-z' 'N-ZA-Mn-za-m'
The password is 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
```
[help 1](https://www.busindre.com/cifrado_cesar_desde_la_terminal_con_tr)


12. level 12
```console
$ ssh bandit12@bandit.labs.overthewire.org -p 2220
// 5Te8Y4drgCRfCx8ugdwuEX8KFC6k2EUu
$ mkdir /tmp/bodhert
$ cp data.txt /tmp/bodhert
$ cd /tmp/bodhert
$ xxd -r data.txt > data
$ file data
data: gzip compressed data, was "data2.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix
$ mv data data2.gz
$ gunzip data2.gz
$ file data2
data2: bzip2 compressed data, block size = 900k
$ mv data2 data2.bz
$ bzip2 -d data2.bz
$ file data2
data2: gzip compressed data, was "data4.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix
$ mv data2 data4.gz
$ gunzip data4.gz
$ file data4
data4: POSIX tar archive (GNU)
$ mv data4 data4.tar
$ tar xvf data4.tar
$ tar xvf data4.tar
data5.bin
$ file data5.bin
data5.bin: POSIX tar archive (GNU)
$ mv data5.bin data5.tar
$ tar xvf data5.tar
data6.bin
$ file data6.bin
data6.bin: bzip2 compressed data, block size = 900k
$ mv data6.bin data6.bz
$ bzip2 -d data6.bz
$ file data6
data6: POSIX tar archive (GNU)
$ mv data6 data6.tar
$ tar xvf data6.tar
data8.bin
$ file data8.bin
data8.bin: gzip compressed data, was "data9.bin", last modified: Thu Dec 28 13:34:36 2017, max compression, from Unix
$ mv data8.bin data8.gz
$ gunzip data8.gz
$ file data8
data8: ASCII text
$ cat data8
The password is 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
```

13. level 13
```console
$ssh bandit13@bandit.labs.overthewire.org -p 2220
// password 8ZjyCRiBWFYkneahHwxCv3wb2a1ORpYL
$cat sshkey.private
-----BEGIN RSA PRIVATE KEY-----
MIIEpAIBAAKCAQEAxkkOE83W2cOT7IWhFc9aPaaQmQDdgzuXCv+ppZHa++buSkN+
gg0tcr7Fw8NLGa5+Uzec2rEg0WmeevB13AIoYp0MZyETq46t+jk9puNwZwIt9XgB
ZufGtZEwWbFWw/vVLNwOXBe4UWStGRWzgPpEeSv5Tb1VjLZIBdGphTIK22Amz6Zb
ThMsiMnyJafEwJ/T8PQO3myS91vUHEuoOMAzoUID4kN0MEZ3+XahyK0HJVq68KsV
ObefXG1vvA3GAJ29kxJaqvRfgYnqZryWN7w3CHjNU4c/2Jkp+n8L0SnxaNA+WYA7
jiPyTF0is8uzMlYQ4l1Lzh/8/MpvhCQF8r22dwIDAQABAoIBAQC6dWBjhyEOzjeA
J3j/RWmap9M5zfJ/wb2bfidNpwbB8rsJ4sZIDZQ7XuIh4LfygoAQSS+bBw3RXvzE
pvJt3SmU8hIDuLsCjL1VnBY5pY7Bju8g8aR/3FyjyNAqx/TLfzlLYfOu7i9Jet67
xAh0tONG/u8FB5I3LAI2Vp6OviwvdWeC4nOxCthldpuPKNLA8rmMMVRTKQ+7T2VS
nXmwYckKUcUgzoVSpiNZaS0zUDypdpy2+tRH3MQa5kqN1YKjvF8RC47woOYCktsD
o3FFpGNFec9Taa3Msy+DfQQhHKZFKIL3bJDONtmrVvtYK40/yeU4aZ/HA2DQzwhe
ol1AfiEhAoGBAOnVjosBkm7sblK+n4IEwPxs8sOmhPnTDUy5WGrpSCrXOmsVIBUf
laL3ZGLx3xCIwtCnEucB9DvN2HZkupc/h6hTKUYLqXuyLD8njTrbRhLgbC9QrKrS
M1F2fSTxVqPtZDlDMwjNR04xHA/fKh8bXXyTMqOHNJTHHNhbh3McdURjAoGBANkU
1hqfnw7+aXncJ9bjysr1ZWbqOE5Nd8AFgfwaKuGTTVX2NsUQnCMWdOp+wFak40JH
PKWkJNdBG+ex0H9JNQsTK3X5PBMAS8AfX0GrKeuwKWA6erytVTqjOfLYcdp5+z9s
8DtVCxDuVsM+i4X8UqIGOlvGbtKEVokHPFXP1q/dAoGAcHg5YX7WEehCgCYTzpO+
xysX8ScM2qS6xuZ3MqUWAxUWkh7NGZvhe0sGy9iOdANzwKw7mUUFViaCMR/t54W1
GC83sOs3D7n5Mj8x3NdO8xFit7dT9a245TvaoYQ7KgmqpSg/ScKCw4c3eiLava+J
3btnJeSIU+8ZXq9XjPRpKwUCgYA7z6LiOQKxNeXH3qHXcnHok855maUj5fJNpPbY
iDkyZ8ySF8GlcFsky8Yw6fWCqfG3zDrohJ5l9JmEsBh7SadkwsZhvecQcS9t4vby
9/8X4jS0P8ibfcKS4nBP+dT81kkkg5Z5MohXBORA7VWx+ACohcDEkprsQ+w32xeD
qT1EvQKBgQDKm8ws2ByvSUVs9GjTilCajFqLJ0eVYzRPaY6f++Gv/UVfAPV4c+S0
kAWpXbv5tbkkzbS0eaLPTKgLzavXtQoTtKwrjpolHKIHUz6Wu+n4abfAIRFubOdN
/+aLoRQ0yBDRbdXMsZN/jvY44eM+xRLdRVyMmdPtP8belRi2E2aEzA==
-----END RSA PRIVATE KEY-----
```

then I copy that to a local file and give them the necesary permissions

```console
$nano keyFor14
//copy the previous key
$chmod 600 keyFor14
$ssh -i keyFor14 bandit14@bandit.labs.overthewire.org -p 2220
```

14. 
```console
$ssh -i keyFor14 bandit14@bandit.labs.overthewire.org -p 2220
$cat /etc/bandit_pass/bandit14 | netcat localhost 30000
Correct!
BfMYroe26WYalil77FoDi9qh59eK5xNr

```

15.
```console
$ssh  bandit15@bandit.labs.overthewire.org -p 2220
//BfMYroe26WYalil77FoDi9qh59eK5xNr 
$cat /etc/bandit_pass/bandit15 | openssl s_client -ign_eof -connect localhost:30001

CONNECTED(00000003)
depth=0 CN = bandit
verify error:num=18:self signed certificate
verify return:1
depth=0 CN = bandit
verify return:1
---
Certificate chain
 0 s:/CN=bandit
   i:/CN=bandit
---
Server certificate
-----BEGIN CERTIFICATE-----
MIICsjCCAZqgAwIBAgIJAKZI1xYeoXFuMA0GCSqGSIb3DQEBCwUAMBExDzANBgNV
BAMMBmJhbmRpdDAeFw0xNzEyMjgxMzIzNDBaFw0yNzEyMjYxMzIzNDBaMBExDzAN
BgNVBAMMBmJhbmRpdDCCASIwDQYJKoZIhvcNAQEBBQADggEPADCCAQoCggEBAOcX
ruVcnQUBeHJeNpSYayQExCJmcHzSCktnOnF/H4efWzxvLRWt5z4gYaKvTC9ixLrb
K7a255GEaUbP/NVFpB/sn56uJc1ijz8u0hWQ3DwVe5ZrHUkNzAuvC2OeQgh2HanV
5LwB1nmRZn90PG1puKxktMjXsGY7f9Yvx1/yVnZqu2Ev2uDA0RXij/T+hEqgDMI7
y4ZFmuYD8z4b2kAUwj7RHh9LUKXKQlO+Pn8hchdR/4IK+Xc4+GFOin0XdQdUJaBD
8quOUma424ejF5aB6QCSE82MmHlLBO2tzC9yKv8L8w+fUeQFECH1WfPC56GcAq3U
IvgdjGrU/7EKN5XkONcCAwEAAaMNMAswCQYDVR0TBAIwADANBgkqhkiG9w0BAQsF
AAOCAQEAnrOty7WAOpDGhuu0V8FqPoKNwFrqGuQCTeqhQ9LP0bFNhuH34pZ0JFsH
L+Y/q4Um7+66mNJUFpMDykm51xLY2Y4oDNCzugy+fm5Q0EWKRwrq+hIM+5hs0RdC
nARP+719ddmUiXF7r7IVP2gK+xqpa8+YcYnLuoXEtpKkrrQCCUiqabltU5yRMR77
3wqB54txrB4IhwnXqpO23kTuRNrkG+JqDUkaVpvct+FAdT3PODMONP/oHII3SH9i
ar/rI9k+4hjlg4NqOoduxX9M+iLJ0Zgj6HAg3EQVn4NHsgmuTgmknbhqTU3o4IwB
XFnxdxVy0ImGYtvmnZDQCGivDok6jA==
-----END CERTIFICATE-----
subject=/CN=bandit
issuer=/CN=bandit
---
No client certificate CA names sent
---
SSL handshake has read 1015 bytes and written 631 bytes
---
New, TLSv1/SSLv3, Cipher is AES128-SHA
Server public key is 2048 bit
Secure Renegotiation IS supported
Compression: NONE
Expansion: NONE
No ALPN negotiated
SSL-Session:
    Protocol  : TLSv1
    Cipher    : AES128-SHA
    Session-ID: 43C923F481C5EA00B32BF1F295338680EA945B3F2BF5938F2EF9A46E1017E242
    Session-ID-ctx:
    Master-Key: 0F7194159CD6FC6625BF4259B45781EB6183AC44C942BAF9723337C952DF8A852A708E277393F6CFC030D6B0B09988FF
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 08 f0 15 a5 d6 6f a0 e8-06 d6 bb a4 0c 33 eb 04   .....o.......3..
    0010 - e9 a3 3a 3b d9 c5 5d b7-08 c1 7c 83 6e 01 63 d1   ..:;..]...|.n.c.
    0020 - f0 8e a9 85 79 16 10 98-f1 32 83 e2 db 4c 5e ab   ....y....2...L^.
    0030 - 6b 37 04 78 22 ac 63 cb-42 25 58 c4 cf 4a 2d 27   k7.x".c.B%X..J-'
    0040 - 7f 23 7d c8 ee 31 aa 8a-bf 13 f1 28 f9 1b d8 f2   .#}..1.....(....
    0050 - 73 83 df 0d 5d d5 e9 a9-2b 3e a1 5b b0 c3 4f e1   s...]...+>.[..O.
    0060 - be 0f 3f 1c 01 72 ab 88-c8 19 97 76 95 ba 29 f7   ..?..r.....v..).
    0070 - 12 50 60 77 7d 63 8a 6a-cb be 54 e0 af 53 31 7a   .P`w}c.j..T..S1z
    0080 - 4a 55 6e 50 8f 83 82 ea-51 80 3f 80 cf 3b 79 8a   JUnP....Q.?..;y.
    0090 - 35 32 e7 b1 14 a3 d0 56-ce 14 cf 32 6f a1 f4 b2   52.....V...2o...

    Start Time: 1529364508
    Timeout   : 300 (sec)
    Verify return code: 18 (self signed certificate)
---
Correct!
cluFn7wTiGryunymYOu4RcffSxQluehd

closed

```