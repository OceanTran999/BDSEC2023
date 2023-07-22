# anyaForger
First, let's see type of file, I saw this is ELF32 file.

![readelf](https://github.com/OceanTran999/BDSEC2023/assets/100577019/0ec68262-df6a-4803-9686-9a7a7374c74d)

Therefore, I would use IDAPro 32-bits to see the full source code of this file. And here is `main()` and `vuln()`:

![mainFunc](https://github.com/OceanTran999/BDSEC2023/assets/100577019/31850714-7384-4a98-a029-91c210ccce13)

![vulnFunc](https://github.com/OceanTran999/BDSEC2023/assets/100577019/cdefe217-0db9-4b22-a2b0-62272f77d8bf)

Then I checked the protection of this file. As the result, the file had no protection.

![checksec](https://github.com/OceanTran999/BDSEC2023/assets/100577019/f3f81cd3-6185-4843-91f5-b684a66c5845)

Next, we will `disassemble vuln`:

I suddenly saw `mov  DWORD PTR [ebp - 0xc], 0x123456678`. Therefore I considered that the address of variable "v1" will be `ebp-0xc`

![v1](https://github.com/OceanTran999/BDSEC2023/assets/100577019/3b4b83ff-da06-4a50-b7db-fe453cb1dd2c)

Next, before call the `gets()` function, I saw there was a code: `lea  eax, [ebp-0x2c]`. Therefore I thought the address of gets() function will be `ebp-0x2c`

![gets](https://github.com/OceanTran999/BDSEC2023/assets/100577019/b6a7e684-951f-40a6-84d3-341225286b74)

After that, I saw the address `ebp-0xc` compare with the value `0xdeadbeef`. So, I realized that I had to overwrite the v1 value to get the flag.

![deadbeef](https://github.com/OceanTran999/BDSEC2023/assets/100577019/92f566b8-740b-42dc-8f10-79794802cac8)

Here is my stack that I drew it.

![stack](https://github.com/OceanTran999/BDSEC2023/assets/100577019/b3fe8d09-288a-4294-9d00-dd021c701db2)

Wakuwaku~~ I finally got the flag

![Flag](https://github.com/OceanTran999/BDSEC2023/assets/100577019/24e27b84-5fc5-428c-979d-ce37573b3a90)

```Sadly :( these 2 challenges I didn't have time to solve, but I will be able to solve it after the competition XD```

# callme



# ghost


