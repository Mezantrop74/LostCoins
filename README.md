# LostCoins
 - This is a modified version [VanitySearch](https://github.com/JeanLucPons/VanitySearch/). 
Huge thanks [kanhavishva](https://github.com/kanhavishva) and to all developers whose codes were used in LostCoins.
## Quick start
- Сonvert addresses into binary hashes RIPEMD160 use [b58dec.exe](https://github.com/phrutis/LostCoins/blob/main/Others/b58dec.exe) Сommand: ```b58dec.exe 1.txt 2.bin```
- It is important to sort the 2.bin file otherwise the Bloom search filter will not work as expected.
- To sort 2.bin use the program [RMD160-Sort.exe](https://github.com/phrutis/LostCoins/blob/main/Others/RMD160-Sort.exe) Сommand: ```RMD160-Sort.exe 2.bin addresse160-Sort.bin``` 
- The minimum number of hashes160 in addresse160-Sort.bin must be at least 1000
- For Multi GPUs use LostCoins.exe -t 0 --gpu --gpux 256,256,256,256 --gpui 0,1 -f test.bin -r 2 -n 64
- Default auto Grid size. Example my RTX2070 in auto -x 256,128 I added LostCoins.exe -t 0 -g -i 0 -x 288,512 the speed has doubled.
- Do not use the GPU+CPU will drop the speed. Run 2 copies of the program one on the CPU and the second on the GPU
- You can search hashes160 of other coins, if it finds it, it will give an empty legacy address and positive private key. Ctrl + C (exit)
## Parametrs:
```
C:\Users\user>LostCoins.exe -h
Usage: LostCoins [options...]
Options:
    -v, --version          Print version. For help visit https://github.com/phrutis/LostCoins
    -c, --check            Check the working of the code LostCoins
    -u, --uncomp           Search only uncompressed addresses
    -b, --both             Search both (uncompressed and compressed addresses)
    -g, --gpu              Enable GPU calculation
    -i, --gpui             GPU ids: 0,1...: List of GPU(s) to use, default is 0
    -x, --gpux             GPU gridsize: g0x,g0y,g1x,g1y, ...: Specify GPU(s) kernel gridsize, default is 8*(MP number),128
    -t, --thread           ThreadNumber: Specify number of CPUs thread, default is number of core
    -o, --out              Outputfile: Output results to the specified file, default: Found.txt
    -m, --max              Specify maximun number of addresses found by each kernel call
    -s, --seed             PassPhrase   (Start bit range)
    -z, --zez              PassPhrase 2 (End bit range)
    -e, --nosse            Disable SSE hash function
    -l, --list             List cuda enabled devices
    -r, --rkey             Number of random modes
    -n, --nbit             Number of letters and number bit range 1-256
    -f, --file             RIPEMD160 binary hash file path
    -d, --diz              Display modes -d 0 [info+count], -d 1 SLOW speed [info+hex+count], Default -d 2 [count] HIGH speed
    -k, --color            Colors: 1-255 Recommended 3, 10, 11, 14, 15, 240 (White-black)
    -h, --help             Shows this pagethis page
 ```
## Mode 1 
### GPU random search between start and end hash
 - For GPU ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 1 -s ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f0000000 -z ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61ffffffff```

 ```
 C:\Users\user>LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 1 -s ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f0000000 -z ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61ffffffff

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : GPU
 CPU THREAD   : 0
 GPU IDS      : 0
 GPU GRIDSIZE : 288x512
 RANDOM MODE  : 1
 ROTOR SPEED  : HIGH (only counter)
 CHARACTERS   : 0
 PASSPHRASE   : ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f0000000
 PASSPHRASE 2 : ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61ffffffff
 DISPLAY MODE : 2
 TEXT COLOR   : 15
 MAX FOUND    : 8
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000001FE8C61C5A0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Fri Aug 27 20:54:08 2021

  Random mode : 1
  Random      : Finding in a ranges
  Global start: BA7816BF8F01CFEA414140DE5DAE2223B00361A396177A9CB410FF61F0000000 (256 bit)
  Global end  : BA7816BF8F01CFEA414140DE5DAE2223B00361A396177A9CB410FF61FFFFFFFF (256 bit)
  Global range: 000000000000000000000000000000000000000000000000000000000FFFFFFF (28 bit)
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

  GPU         : GPU #0 NVIDIA GeForce RTX 2070 (36x64 cores) Grid(288x512)

 [00:00:22] [CPU+GPU: 1223,71 Mk/s] [GPU: 1223,71 Mk/s] [T: 27,179,089,920] [F: 0]

=================================================================================
* PubAddress: 1PoQRMsXyQFSqCCRek7tt7umfRkJG9TY8x
* Priv (WIF): p2pkh: L3UBXym7JYcMX91ssLgZzS2MvxTxjU3VRf9S4jJWXVFdDi4NsLcm
* Priv (HEX): BA7816BF8F01CFEA414140DE5DAE2223B00361A396177A9CB410FF61F20015AD
=================================================================================

 [00:00:24] [CPU+GPU: 1224,19 Mk/s] [GPU: 1224,19 Mk/s] [T: 29,896,998,912] [F: 1]

=================================================================================
* PubAddress: 1PoQRMsXyQFSqCCRek7tt7umfRkJG9TY8x
* Priv (WIF): p2pkh: L3UBXym7JYcMX91ssLgZzS2MvxTxjU3VRf9S4jJWXVFdDi4NsLcm
* Priv (HEX): BA7816BF8F01CFEA414140DE5DAE2223B00361A396177A9CB410FF61F20015AD
=================================================================================



=================================================================================
* PubAddress: 1PoQRMsXyQFSqCCRek7tt7umfRkJG9TY8x
* Priv (WIF): p2pkh: L3UBXym7JYcMX91ssLgZzS2MvxTxjU3VRf9S4jJWXVFdDi4NsLcm
* Priv (HEX): BA7816BF8F01CFEA414140DE5DAE2223B00361A396177A9CB410FF61F20015AD
=================================================================================

 [00:00:30] [CPU+GPU: 1141,40 Mk/s] [GPU: 1141,40 Mk/s] [T: 35,332,816,896] [F: 3]

=================================================================================
* PubAddress: 1PoQRMsXyQFSqCCRek7tt7umfRkJG9TY8x
* Priv (WIF): p2pkh: L3UBXym7JYcMX91ssLgZzS2MvxTxjU3VRf9S4jJWXVFdDi4NsLcm
* Priv (HEX): BA7816BF8F01CFEA414140DE5DAE2223B00361A396177A9CB410FF61F20015AD
=================================================================================

 [00:00:32] [CPU+GPU: 1139,89 Mk/s] [GPU: 1139,89 Mk/s] [T: 37,144,756,224] [F: 4]

BYE
 ```
 ### CPU random search between start and end hash
  - For CPU ```LostCoins.exe -t 6 -f test.bin -r 1 -s ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f0000000 -z ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61ffffffff```
 ```
C:\Users\user>LostCoins.exe -t 6 -f test.bin -r 1 -s ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f0000000 -z ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61ffffffff

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : CPU
 CPU THREAD   : 6
 GPU IDS      : 0
 GPU GRIDSIZE : -1x128
 RANDOM MODE  : 1
 ROTOR SPEED  : HIGH (only counter)
 CHARACTERS   : 0
 PASSPHRASE   : ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f0000000
 PASSPHRASE 2 : ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61ffffffff
 DISPLAY MODE : 2
 TEXT COLOR   : 15
 MAX FOUND    : 8
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000001BB4D2AD670
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Fri Aug 27 20:58:48 2021

  Random mode : 1
  Random      : Finding in a ranges
  Global start: BA7816BF8F01CFEA414140DE5DAE2223B00361A396177A9CB410FF61F0000000 (256 bit)
  Global end  : BA7816BF8F01CFEA414140DE5DAE2223B00361A396177A9CB410FF61FFFFFFFF (256 bit)
  Global range: 000000000000000000000000000000000000000000000000000000000FFFFFFF (28 bit)
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

 [00:24:24] [CPU+GPU: 10,49 Mk/s] [GPU: 0,00 Mk/s] [T: 14,947,074,048] [F: 0]
 ```
 ## Mode 2
 ### Exact accurate bit by bit search in a range
 - For GPU ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 2 -n 64```
 ```
C:\Users\user>LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 2 -n 64

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : GPU
 CPU THREAD   : 0
 GPU IDS      : 0
 GPU GRIDSIZE : 288x512
 RANDOM MODE  : 2
 ROTOR SPEED  : HIGH (only counter)
 CHARACTERS   : 64
 PASSPHRASE   :
 PASSPHRASE 2 :
 DISPLAY MODE : 2
 TEXT COLOR   : 15
 MAX FOUND    : 8
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 00000166FA9DD4F0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Sat Aug 28 11:18:24 2021

  Random mode : 2
  Random      : Finding in a range
  Use range   : 64 (bit)
  Rotor       : Random generate hex in range 64
  Rotor GPU   : Reloading starting hashes in range 64 (bit) every 100.000.000.000 on the counter
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

  GPU         : GPU #0 NVIDIA GeForce RTX 2070 (36x64 cores) Grid(288x512)

 [00:00:26] [CPU+GPU: 1215,44 Mk/s] [GPU: 1215,44 Mk/s] [T: 31,708,938,240] [F: 0]
 ```
  ### Exact accurate bit by bit search in a range 
 - For CPU ```LostCoins.exe -t 6 -f test.bin -r 2 -n 64 -d 2``` Speed
 - For CPU ```LostCoins.exe -t 6 -f test.bin -r 2 -n 64 -d 0``` Normal
 - For CPU ```LostCoins.exe -t 6 -f test.bin -r 2 -n 64 -d 1``` Slow
  ```
  C:\Users\user>LostCoins.exe -t 6 -f test.bin -r 2 -n 64 -d 1

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : CPU
 CPU THREAD   : 6
 GPU IDS      : 0
 GPU GRIDSIZE : -1x128
 RANDOM MODE  : 2
 ROTOR SPEED  : VERY SLOW (info+hashes+counter are displayed)
 CHARACTERS   : 64
 PASSPHRASE   :
 PASSPHRASE 2 :
 DISPLAY MODE : 1
 TEXT COLOR   : 15
 MAX FOUND    : 8
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000001ABE41DD5D0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Fri Aug 27 20:27:54 2021

  Random mode : 2
  Random      : Finding in a range
  Use range   : 64 (bit)
  Rotor       : Random generate hex in range 64
  Rotor CPU   : 6 cores constant random generation hashes in 64 (bit) range
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

 [C5388EB5509D77A9] (64 bit)                                                          [00:00:34] [CPU+GPU: 10,71 Mk/s] [GPU: 0,00 Mk/s] [T: 379,490,304] [F: 0]
  ```
 ## Mode 3
 ### Search privat key (part+ -n values +par2 + -n value)
 - Run GPU: ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 3 -s 0123456789abcdef -n 10 -z fedcba9876543210 -m 5 -d 2```
 - Examples others combinations:
 - Run GPU: ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 3 -n 10 -z fedcba9876543210 -m 5 -d 0```
 - Run GPU: ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 3 -s 0123456789abcdef -z fedcba9876543210 -m 9 -d 0``` 
 - Run GPU: ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 3 -s 0123456789abcdeffedcba9876543210 -m 20 -d 0```
 
 ```
 C:\Users\user>LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 3 -s 0123456789abcdef -n 10 -z fedcba9876543210 -m 5 -d 0

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : GPU
 CPU THREAD   : 0
 GPU IDS      : 0
 GPU GRIDSIZE : 288x512
 RANDOM MODE  : 3
 ROTOR SPEED  : SLOW (info+counter are displayed)
 CHARACTERS   : 10
 PASSPHRASE   : 0123456789abcdef
 PASSPHRASE 2 : fedcba9876543210
 DISPLAY MODE : 0
 TEXT COLOR   : 15
 MAX FOUND    : 5
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000001F5A6C0C1B0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Fri Aug 27 20:37:25 2021

  Random mode : 3
  Random      : Part+value+part2+value
  Part        : 0123456789abcdef
  Value       : 10 x (0-f)
  Part 2      : fedcba9876543210
  Value 2     : 5 x (0-f)
  Example     : 0123456789abcdef[<<10>>]fedcba9876543210[<<5>>]
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

  GPU         : GPU #0 NVIDIA GeForce RTX 2070 (36x64 cores) Grid(288x512)

 [0123456789abcdef029c91aeaefedcba987654321042b1d]
 ```
 ### Search privat key (part+ -n values +par2 + -n value)
  - Run CPU: ```LostCoins.exe -t 6 -f test.bin -r 3 -s 0123456789abcdef -n 10 -z fedcba9876543210 -m 5 -d 0```
 ```
C:\Users\user>LostCoins.exe -t 6 -f test.bin -r 3 -s 0123456789abcdef -n 10 -z fedcba9876543210 -m 5 -d 0

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : CPU
 CPU THREAD   : 6
 GPU IDS      : 0
 GPU GRIDSIZE : -1x128
 RANDOM MODE  : 3
 ROTOR SPEED  : SLOW (info+counter are displayed)
 CHARACTERS   : 10
 PASSPHRASE   : 0123456789abcdef
 PASSPHRASE 2 : fedcba9876543210
 DISPLAY MODE : 0
 TEXT COLOR   : 15
 MAX FOUND    : 5
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 0000022BC7B1D2D0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Fri Aug 27 20:51:30 2021

  Random mode : 3
  Random      : Part+value+part2+value
  Part        : 0123456789abcdef
  Value       : 10 x (0-f)
  Part 2      : fedcba9876543210
  Value 2     : 5 x (0-f)
  Example     : 0123456789abcdef[<<10>>]fedcba9876543210[<<5>>]
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

 [0123456789abcdef8a76254fa7fedcba987654321093150] [00:00:44] [CPU+GPU: 10,72 Mk/s] [GPU: 0,00 Mk/s] [T: 476,338,176] [F: 0]
 ```
  ## Mode 4
  ### Exact random search between specified ranges
 - Run GPU ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 4 -s 64 -z 72```
 - Run CPU ```LostCoins.exe -t 6 -f test.bin -r 4 -s 64 -z 256```
 ```
C:\Users\user>LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 4 -s 64 -z 72

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : GPU
 CPU THREAD   : 0
 GPU IDS      : 0
 GPU GRIDSIZE : 288x512
 RANDOM MODE  : 4
 ROTOR SPEED  : HIGH (only counter)
 CHARACTERS   : 0
 PASSPHRASE   : 64
 PASSPHRASE 2 : 72
 DISPLAY MODE : 2
 TEXT COLOR   : 15
 MAX FOUND    : 8
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 00000285064CB6E0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Fri Aug 27 21:25:05 2021

  Random mode : 4
  Random      : Finding in a ranges
  Start range : 64 (bit)
  End range   : 72 (bit)
  Rotor       : Generate random hex in ranges 64 <~> 72
  Rotor GPU   : Reloading new starting hashes in ranges every 100.000.000.000 on the counter
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

  GPU         : GPU #0 NVIDIA GeForce RTX 2070 (36x64 cores) Grid(288x512)

 [00:01:19] [CPU+GPU: 1112,32 Mk/s] [GPU: 1112,32 Mk/s] [T: 92,408,905,728] [F: 0]
 ```
 ## Mode 5
 #### GPU Mnemonic 12 random words (bip39)
 - Run GPU: ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 5 -d 2```
 - TEST only ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 5 -d 1``` Slow

```
C:\Users\user>LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 5 -d 2

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : GPU
 CPU THREAD   : 0
 GPU IDS      : 0
 GPU GRIDSIZE : 288x512
 RANDOM MODE  : 5
 ROTOR SPEED  : HIGH (only counter)
 CHARACTERS   : 0
 PASSPHRASE   :
 PASSPHRASE 2 :
 DISPLAY MODE : 2
 TEXT COLOR   : 15
 MAX FOUND    : 8
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000002C57125CB30
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Fri Aug 27 20:04:18 2021

  Random mode : 5
  Using       : Mnemonic (bip39)
  List        : 2048 words
  Rotor       : Generation of 12 random words
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

  GPU         : GPU #0 NVIDIA GeForce RTX 2070 (36x64 cores) Grid(288x512)

 [00:00:34] [CPU+GPU: 1320,45 Mk/s] [GPU: 1320,45 Mk/s] [T: 44,674,604,544] [F: 0]
```

 #### CPU Mnemonic 12 random words (bip39)
 - Run CPU: ```LostCoins.exe -t 6 -f test.bin -r 5 -d 2``` Speed  (only counter)
 - Run CPU: ```LostCoins.exe -t 6 -f test.bin -r 5 -d 0``` Normal (info+counter)
 - Run CPU: ```LostCoins.exe -t 6 -f test.bin -r 5 -d 1``` Slow  (info+hex+counter)
 
 ```
C:\Users\user>LostCoins.exe -t 6 -f test.bin -r 5 -d 1

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : CPU
 CPU THREAD   : 6
 GPU IDS      : 0
 GPU GRIDSIZE : -1x128
 RANDOM MODE  : 5
 ROTOR SPEED  : VERY SLOW (info+hashes+counter are displayed)
 CHARACTERS   : 0
 PASSPHRASE   :
 PASSPHRASE 2 :
 DISPLAY MODE : 1
 TEXT COLOR   : 15
 MAX FOUND    : 8
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 0000020B050ED080
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Fri Aug 27 20:09:11 2021

  Random mode : 5
  Using       : Mnemonic (bip39)
  List        : 2048 words
  Rotor       : Generation of 12 random words
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

 [seat toilet all attend need ghost direct rival fold fault once virus] [488E1BCEED165888124686F4BDCFEC2CEBDA9F79B5CAB82442A091A66F873B8F]  310,167,552] [F: 0]
 ```
## Mode 6 
#### VanitySearch generator +-~ 4 bit. Reloads random starting points in a given range every 100.000.000.000 on the counter
Run GPU:  ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 6 -n 256 ```
 ```
C:\Users\user>LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 6 -n 256

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : GPU
 CPU THREAD   : 0
 GPU IDS      : 0
 GPU GRIDSIZE : 288x512
 RANDOM MODE  : 6
 ROTOR SPEED  : HIGH (only counter)
 CHARACTERS   : 256
 PASSPHRASE   :
 PASSPHRASE 2 :
 DISPLAY MODE : 2
 TEXT COLOR   : 15
 MAX FOUND    : 8
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000001C300C0D860
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Fri Aug 27 19:12:08 2021

  Random mode : 6
  Rotor GPU   : Reloading new starting hashes in range every 100.000.000.000 on the counter
  Range bit   : 256 (bit) Recommended -n 256 (256 searches in the 252-256 range and below)
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

  GPU         : GPU #0 NVIDIA GeForce RTX 2070 (36x64 cores) Grid(288x512)

 [00:32:28] [CPU+GPU: 1009,71 Mk/s] [GPU: 1009,71 Mk/s] [T: 1,898,006,446,080] [F: 0]
 ```
 #### For CPU Constant generation random new hashes in a given range +- ~ 4 bit
 - Run CPU:  ```LostCoins.exe -t 6 -f test.bin -r 0 -n 256 ```
 ```
C:\Users\user>LostCoins.exe -t 6 -f test.bin -r 6 -n 256 -d 1

 LostCoins v2.1

 SEARCH MODE  : COMPRESSED
 DEVICE       : CPU
 CPU THREAD   : 6
 GPU IDS      : 0
 GPU GRIDSIZE : -1x128
 RANDOM MODE  : 6
 ROTOR SPEED  : VERY SLOW (info+hashes+counter are displayed)
 CHARACTERS   : 256
 PASSPHRASE   :
 PASSPHRASE 2 :
 DISPLAY MODE : 1
 TEXT COLOR   : 15
 MAX FOUND    : 8
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000001FE264FCDA0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Fri Aug 27 19:47:26 2021

  Random mode : 6
  Rotor CPU   : 6 cores constant random generation hashes in range 256 (bit)
  Range bit   : 256 (bit) Recommended -n 256 (256 searches in the 252-256 range and below)
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

 (255 bit) [494293D26D905A0F268AD5AC2A921DEF8CFF3ECFC9794DF3E4D0B39E651BE942]         [00:01:35] [CPU+GPU: 10,56 Mk/s] [GPU: 0,00 Mk/s] [T: 1,029,347,328] [F: 0]
 ```
## Modes 7-56 (additional)
### Find LostCoins using a random passphrases 
- [**List of additional 7-56 modes**](https://github.com/phrutis/LostCoins/blob/main/Others/Modes.md)

## Building
- Microsoft Visual Studio Community 2019
- CUDA version [**10.22**](https://developer.nvidia.com/cuda-10.2-download-archive?target_os=Windows&target_arch=x86_64&target_version=10&target_type=exenetwork)
## Donation
- BTC: bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9
## License
LostCoins is licensed under GPL v3.0
## Disclaimer
ALL THE CODES, PROGRAM AND INFORMATION ARE FOR EDUCATIONAL PURPOSES ONLY. USE IT AT YOUR OWN RISK. THE DEVELOPER WILL NOT BE RESPONSIBLE FOR ANY LOSS, DAMAGE OR CLAIM ARISING FROM USING THIS PROGRAM.
