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

