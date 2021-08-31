# LostCoins v2.02
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
    -m, --max              Number 1-10000 For GPU Reloads random started hashes every billion in counter. Default: 100 billion
    -s, --seed             PassPhrase   (Start bit range)
    -z, --zez              PassPhrase 2 (End bit range)
    -l, --list             List cuda enabled devices
    -r, --rkey             Number of random modes
    -n, --nbit             Number of letters and number bit range 1-256
    -f, --file             RIPEMD160 binary hash file path
    -d, --diz              Display modes -d 0 [info+count], -d 1 SLOW speed [info+hex+count], Default -d 2 [count] HIGH speed
    -k, --color            Colors: 1-255 Recommended 3, 10, 11, 14, 15, 240 (White-black)
    -h, --help             Shows this page

C:\Users\user>
 ```
## Mode 0 
## Find Passphrases and Privat keys from a text file
### Passphrases from a file
 - To search for passphrases, use mode **-u** or **-b** for old Lost Coins 
 - Each password on a new line. The address in base.bin must be no more than **2,000,000** 
 - If the base is larger, there will be false positive error addresses 
 - Don't use a Multicores, works only single core -t 1 GPU not supported. 
 - For CPU (NORMAL) ```LostCoins.exe -t 1 -f test.bin -r 0 -s Base-passphrases.txt``` 
 - For CPU (SLOW) ```LostCoins.exe -t 1 -f test.bin -r 0 -s Base-passphrases.txt -d 0```
 - For CPU (Very SLOW)  ```LostCoins.exe -t 1 -f test.bin -r 0 -s Base-passphrases.txt -d 1```
```
C:\Users\user>LostCoins.exe -t 1 -f test.bin -r 0 -s Base-passphrases.txt

 LostCoins v2.2

 SEARCH MODE  : COMPRESSED
 DEVICE       : CPU
 CPU THREAD   : 1
 GPU IDS      : 0
 GPU GRIDSIZE : -1x128
 RANDOM MODE  : 0
 ROTOR SPEED  : HIGH (only counter)
 CHARACTERS   : 0
 PASSPHRASE   : Base-passphrases.txt
 PASSPHRASE 2 :
 DISPLAY MODE : 2
 TEXT COLOR   : 15
 GPU REKEY    : 100000000000
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 0000024DC752C740
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Mon Aug 30 13:01:50 2021

  Random mode : 0
  Rotor       : Loading passphrases from file: Base-passphrases.txt ...
  Loaded      : 38361753 passphrases
  Rotor       : Runs on a single core. Don't use a multicores, only -t 1
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

 [00:12:37] [CPU+GPU: 0,02 Mk/s] [GPU: 0,00 Mk/s] [T: 20,474,168] [F: 0]

=================================================================================
* PubAddress: 1PoQRMsXyQFSqCCRek7tt7umfRkJG9TY8x
* Priv (WIF): p2pkh: L3UBXym7JYcMX91ssLgZzS2MvxTxjU3VRf9S4jJWXVFdDi4NsLcm
* Priv (HEX): BA7816BF8F01CFEA414140DE5DAE2223B00361A396177A9CB410FF61F20015AD
=================================================================================

 [00:15:57] [CPU+GPU: 0,03 Mk/s] [GPU: 0,00 Mk/s] [T: 25,966,367] [F: 1]

=================================================================================
* PubAddress: 15KqNGHFEViRS4WTYYJ4TRoDtSXH5ESzW9
* Priv (WIF): p2pkh: L3BEabkqcsppnTdzAWiizPEuf3Rvr8QEac21uRVsYb9hjesWBxuF
* Priv (HEX): B1C02B717C94BD4243E83B5E98BA37FB273BC035E4AD8FC438EA4D07A1043F56
=================================================================================

 [00:19:48] [CPU+GPU: 0,03 Mk/s] [GPU: 0,00 Mk/s] [T: 32,191,853] [F: 2]

=================================================================================
* PubAddress: 14Nmb7rFFLdZhKaud5h7nDSLFQfma7JCz2
* Priv (WIF): p2pkh: L31UCqx296TVRtgpCJspQJYHkwUeA4o3a2pvYKwRrCCAmi2NirDG
* Priv (HEX): ACBA25512100F80B56FC3CCD14C65BE55D94800CDA77585C5F41A887E398F9BE
=================================================================================

 [00:23:43] [CPU+GPU: 0,03 Mk/s] [GPU: 0,00 Mk/s] [T: 38,321,171] [F: 3]

=================================================================================
* PubAddress: 1Mfw1us14DXJ8ju88iewjt48tswqEshU62
* Priv (WIF): p2pkh: KyiR31LZTQ2hk1DRxEticnsQCA8tjFZcgJiKNaRArZME5fpfAjWj
* Priv (HEX): 4A70FE9AA6436E02C2DEA340FBD1E352E4EF2D8CE6CA52AD25D4B95471FC8BF2
=================================================================================

BYE
```
### Privat keys from a file
 - For CPU (NORMAL) ```LostCoins.exe -t 1 -f test.bin -r 0 -s private-keys.txt -z keys``` 
 - For CPU (SLOW) ```LostCoins.exe -t 1 -f test.bin -r 0 -s private-keys.txt -z keys -d 0```
 - For CPU (Very SLOW)  ```LostCoins.exe -t 1 -f test.bin -r 0 -s private-keys.txt -z keys -d 1```
 - Private key (HEX) looks like this only numbers 0-9 and letters a,b,c,d,e,f on a new line. 
 - Example: 4A70FE9AA6436E02C2DEA340FBD1E352E4EF2D8CE6CA52AD25D4B95471FC8BF2
 - Each Private keys on a new line. The address in base.bin must be no more than **2,000,000** 
 - If the base is larger, there will be false positive error addresses  
 - Don't use a Multicores, works only single core -t 1 GPU not supported.
```
C:\Users\user>LostCoins.exe -b -t 1 -f test.bin -r 0 -s private-keys.txt -z keys

 LostCoins v2.2

 SEARCH MODE  : COMPRESSED & UNCOMPRESSED
 DEVICE       : CPU
 CPU THREAD   : 1
 GPU IDS      : 0
 GPU GRIDSIZE : -1x128
 RANDOM MODE  : 0
 ROTOR SPEED  : HIGH (only counter)
 CHARACTERS   : 0
 PASSPHRASE   : private-keys.txt
 PASSPHRASE 2 : keys
 DISPLAY MODE : 2
 TEXT COLOR   : 15
 GPU REKEY    : 100000000000
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 00000180F514CDC0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Mon Aug 30 19:32:34 2021

  Random mode : 0
  Rotor       : Loading private keys from file: private-keys.txt ...
  Loaded      : 1555209 private keys
  Rotor       : Runs on a single core. Don't use a multicores, only -t 1
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9


=================================================================================
* PubAddress: 162TRPRZvdgLVNksMoMyGJsYBfYtB4Q8tM
* Priv (WIF): p2pkh: 5JiznUZskJpwodP3SR85vx5JKeopA3QpTK63BuziW8RmGGyJg81
* Priv (HEX): 77AF778B51ABD4A3C51C5DDD97204A9C3AE614EBCCB75A606C3B6865AED6744E
=================================================================================

 [00:00:02] [CPU+GPU: 0,03 Mk/s] [GPU: 0,00 Mk/s] [T: 69,624] [F: 1]

=================================================================================
* PubAddress: 1ERNpuxsGB6ytQKTwtCSmeyBTzmyw3uQAG
* Priv (WIF): p2pkh: 5KMdQbcUFS3PBbC6VgitFrFuaca3gBY4BJt4jpQ2YTNdPZ1CbuE
* Priv (HEX): CADC8EDAB738C1DF2CE192AF17E7D35EBBDCAF075E32ED2CC86F6D97C160DBAE
=================================================================================

 [00:00:10] [CPU+GPU: 0,03 Mk/s] [GPU: 0,00 Mk/s] [T: 300,708] [F: 2]

=================================================================================
* PubAddress: 19JxMTT1YqVHAx16NdvgULNajRYvrbFjm1
* Priv (WIF): p2pkh: 5HwfeuhdFscL9YTQCLT2952dieZEtKbzJ328b4CR1v6YUVLu2D7
* Priv (HEX): 10C22BCF4C768B515BE4E94BCAFC71BF3E8FB5F70B2584BCC8C7533217F2E7F9
=================================================================================

 [00:00:14] [CPU+GPU: 0,03 Mk/s] [GPU: 0,00 Mk/s] [T: 415,310] [F: 3]

=================================================================================
* PubAddress: 1Pk2zGBd4a7oUFY61JjXHLgzrH6Hqpartv
* Priv (WIF): p2pkh: 5KjekXVo3FPheAiXCJkuXJBu9WLfNxe5o35jYjLBZb8H53jJ2sT
* Priv (HEX): FCDE2B2EDBA56BF408601FB721FE9B5C338D10EE429EA04FAE5511B68FBF8FB9
=================================================================================

 [00:00:22] [CPU+GPU: 0,03 Mk/s] [GPU: 0,00 Mk/s] [T: 647,241] [F: 4]

=================================================================================
* PubAddress: 1FFtUDpR2CYZDc9TxzNpbNP1U6cXQ9Lq5c
* Priv (WIF): p2pkh: 5J9J63iW7s5p54T569qstediqNgBTLXpUmxUtQwsXTaHz3JCsKt
* Priv (HEX): 2B2961A431B23C9007EFE270C1D7EB79C19D4192D7CD2D924176EB0B19E7D2A1
=================================================================================

 [00:00:26] [CPU+GPU: 0,03 Mk/s] [GPU: 0,00 Mk/s] [T: 761,551] [F: 5]

=================================================================================
* PubAddress: 1PoQRMsXyQFSqCCRek7tt7umfRkJG9TY8x
* Priv (WIF): p2pkh: L3UBXym7JYcMX91ssLgZzS2MvxTxjU3VRf9S4jJWXVFdDi4NsLcm
* Priv (HEX): BA7816BF8F01CFEA414140DE5DAE2223B00361A396177A9CB410FF61F20015AD
=================================================================================

 [00:00:36] [CPU+GPU: 0,03 Mk/s] [GPU: 0,00 Mk/s] [T: 1,041,287] [F: 6]

=================================================================================
* PubAddress: 14Nmb7rFFLdZhKaud5h7nDSLFQfma7JCz2
* Priv (WIF): p2pkh: L31UCqx296TVRtgpCJspQJYHkwUeA4o3a2pvYKwRrCCAmi2NirDG
* Priv (HEX): ACBA25512100F80B56FC3CCD14C65BE55D94800CDA77585C5F41A887E398F9BE
=================================================================================

 [00:00:52] [CPU+GPU: 0,03 Mk/s] [GPU: 0,00 Mk/s] [T: 1,505,264] [F: 7]

=================================================================================
* PubAddress: 1Mfw1us14DXJ8ju88iewjt48tswqEshU62
* Priv (WIF): p2pkh: KyiR31LZTQ2hk1DRxEticnsQCA8tjFZcgJiKNaRArZME5fpfAjWj
* Priv (HEX): 4A70FE9AA6436E02C2DEA340FBD1E352E4EF2D8CE6CA52AD25D4B95471FC8BF2
=================================================================================



BYE
```
## Mode 1 
### GPU random search between start and end hash
 - For GPU ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 1 -s ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61f0000000 -z ba7816bf8f01cfea414140de5dae2223b00361a396177a9cb410ff61ffffffff -m 250```

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
 - For GPU ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 2 -n 64 -m 99```
 ```
C:\Users\user>LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 2 -n 64 -m 99

 LostCoins v2.2

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
 GPU REKEY    : 99000000000
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000002483D4BD9E0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Mon Aug 30 20:07:53 2021

  Random mode : 2
  Random      : Finding in a range
  Use range   : 64 (bit)
  Rotor       : Random generate hex in range 64
  Rotor GPU   : Reloading starting hashes in range 64 (bit) every 99.000.000.000 on the counter
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

  GPU         : GPU #0 NVIDIA GeForce RTX 2070 (36x64 cores) Grid(288x512)

 [00:00:50] [CPU+GPU: 1117,89 Mk/s] [GPU: 1117,89 Mk/s] [T: 58,888,028,160] [F: 0]
 ```
  ### Exact accurate bit by bit search in a range 
 - For CPU ```LostCoins.exe -t 6 -f test.bin -r 2 -n 64 -d 2``` Speed
 - For CPU ```LostCoins.exe -t 6 -f test.bin -r 2 -n 64 -d 0``` Normal
 - For CPU ```LostCoins.exe -t 6 -f test.bin -r 2 -n 64 -d 1``` Slow
  ```
  C:\Users\user>LostCoins.exe -t 6 -f test.bin -r 2 -n 64 -d 1

 LostCoins v2.2

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
 GPU REKEY    : 100000000000
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 0000026D164FA970
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Mon Aug 30 20:09:46 2021

  Random mode : 2
  Random      : Finding in a range
  Use range   : 64 (bit)
  Rotor       : Random generate hex in range 64
  Rotor CPU   : 6 cores constant random generation hashes in 64 (bit) range
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

 [CA0E086D2926ED9C] (64 bit)                                                           [00:00:08] [CPU+GPU: 18,09 Mk/s] [GPU: 0,00 Mk/s] [T: 146,325,504] [F: 0]
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

 LostCoins v2.2

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
 GPU REKEY    : 5000000000
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000002414C2BA720
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Mon Aug 30 20:15:15 2021

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

 [0123456789abcdef3b9aa1788ffedcba987654321082fa5]
 ```
 ### Search privat key (part+ -n values +par2 + -n value)
  - Run CPU: ```LostCoins.exe -t 6 -f test.bin -r 3 -s 0123456789abcdef -n 10 -z fedcba9876543210 -m 5 -d 0```
 ```
C:\Users\user>LostCoins.exe -t 6 -f test.bin -r 3 -s 0123456789abcdef -n 10 -z fedcba9876543210 -m 5 -d 0

 LostCoins v2.2

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
 GPU REKEY    : 5000000000
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 0000021C03E5B6C0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Mon Aug 30 20:16:03 2021

  Random mode : 3
  Random      : Part+value+part2+value
  Part        : 0123456789abcdef
  Value       : 10 x (0-f)
  Part 2      : fedcba9876543210
  Value 2     : 5 x (0-f)
  Example     : 0123456789abcdef[<<10>>]fedcba9876543210[<<5>>]
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

 [0123456789abcdefa9292d9c0efedcba987654321059590]  [00:00:14] [CPU+GPU: 17,54 Mk/s] [GPU: 0,00 Mk/s] [T: 249,544,704] [F: 0]
 ```
  ## Mode 4 (BEST)
  ### Exact random search between specified ranges
 - Run GPU ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 4 -s 64 -z 72 -m 155```
 - Run CPU ```LostCoins.exe -t 6 -f test.bin -r 4 -s 64 -z 256```
 ```
C:\Users\user>LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 4 -s 64 -z 72 -m 155

 LostCoins v2.2

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
 GPU REKEY    : 155000000000
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000001A3E21DC5B0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Mon Aug 30 20:16:55 2021

  Random mode : 4
  Random      : Finding in a ranges
  Start range : 64 (bit)
  End range   : 72 (bit)
  Rotor       : Generate random hex in ranges 64 <~> 72
  Rotor GPU   : Reloading new starting hashes in ranges every 155.000.000.000 on the counter
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

  GPU         : GPU #0 NVIDIA GeForce RTX 2070 (36x64 cores) Grid(288x512)

 [00:00:34] [CPU+GPU: 1230,54 Mk/s] [GPU: 1230,54 Mk/s] [T: 41,674,604,544] [F: 0]
 ```
 ## Mode 5
 #### GPU Mnemonic 12 random words (bip39)
 - Run GPU: ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 5 -d 2```
 - TEST only ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 5 -d 0``` Slow
 - TEST only ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 5 -d 1``` Very Slow
```
LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 5 -d 0

 LostCoins v2.2

 SEARCH MODE  : COMPRESSED
 DEVICE       : GPU
 CPU THREAD   : 0
 GPU IDS      : 0
 GPU GRIDSIZE : 288x512
 RANDOM MODE  : 5
 ROTOR SPEED  : SLOW (info+counter are displayed)
 CHARACTERS   : 0
 PASSPHRASE   :
 PASSPHRASE 2 :
 DISPLAY MODE : 0
 TEXT COLOR   : 15
 GPU REKEY    : 100000000000
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 00000172C3F7E0C0
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Mon Aug 30 20:19:36 2021

  Random mode : 5
  Using       : Mnemonic (bip39)
  List        : 2048 words
  Rotor       : Generation of 12 random words
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

  GPU         : GPU #0 NVIDIA GeForce RTX 2070 (36x64 cores) Grid(288x512)

 [cereal river purchase abstract rack cactus visit crew sorry energy turic rifle]
```

 #### CPU Mnemonic 12 random words (bip39)
 - Run CPU: ```LostCoins.exe -t 6 -f test.bin -r 5 -d 2``` Speed  (only counter)
 - Run CPU: ```LostCoins.exe -t 6 -f test.bin -r 5 -d 0``` Normal (info+counter)
 - Run CPU: ```LostCoins.exe -t 6 -f test.bin -r 5 -d 1``` Slow  (info+hex+counter)
 
 ```
C:\Users\user>LostCoins.exe -t 6 -f test.bin -r 5 -d 1

 LostCoins v2.2

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
 GPU REKEY    : 100000000000
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 0000020B6024D480
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Mon Aug 30 20:21:20 2021

  Random mode : 5
  Using       : Mnemonic (bip39)
  List        : 2048 words
  Rotor       : Generation of 12 random words
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

 [slight fold just legend version wrong silly electric draw script illness genuine] [4B08BA1060C8B3FD6012A31F30FE44D7267277FEBB2EDAA229A349A068A3F8C4] 2] [F: 0]
 ```
## Mode 6 
#### VanitySearch generator +-~ 4 (bit)
Run GPU:  ```LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 6 -n 256 -m 500```
 ```
C:\Users\user>LostCoins.exe -t 0 -g -i 0 -x 288,512 -f test.bin -r 6 -n 256 -m 500

 LostCoins v2.2

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
 GPU REKEY    : 500000000000
 HASH160 FILE : test.bin
 OUTPUT FILE  : Found.txt

 Loading      : 100 %
 Loaded       : 75,471 address

Bloom at 000002977F55B960
  Version     : 2.1
  Entries     : 150942
  Error       : 0,0000010000
  Bits        : 4340363
  Bits/Elem   : 28,755175
  Bytes       : 542546 (0 MB)
  Hash funcs  : 20

  Start Time  : Mon Aug 30 20:25:55 2021

  Random mode : 6
  Rotor GPU   : Reloading new starting hashes in range every 500.000.000.000 on the counter
  Range bit   : 256 (bit) Recommended -n 256 (256 searches in the 252-256 range and below)
  Site        : https://github.com/phrutis/LostCoins
  Donate      : bc1qh2mvnf5fujg93mwl8pe688yucaw9sflmwsukz9

  GPU         : GPU #0 NVIDIA GeForce RTX 2070 (36x64 cores) Grid(288x512)

 [00:00:18] [CPU+GPU: 1231,17 Mk/s] [GPU: 1231,17 Mk/s] [T: 21,743,271,936] [F: 0]
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
