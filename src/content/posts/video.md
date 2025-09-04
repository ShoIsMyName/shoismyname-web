---
title: Include Video in the Posts
published: 2023-08-01
description: This post demonstrates how to include embedded video in a blog post.
tags: [Example, Video]
category: Examples
draft: false
---

Just copy the embed code from YouTube or other platforms, and paste it in the markdown file.

```yaml
---
title: Include Video in the Post
published: 2023-10-19
// ...
---

<iframe width="100%" height="468" src="https://www.youtube.com/embed/5gIf0_xpFPI?si=N1WTorLKL0uwLsU_" title="YouTube video player" frameborder="0" allowfullscreen></iframe>
```

## YouTube

<iframe width="100%" height="468" src="https://www.youtube.com/embed/5gIf0_xpFPI?si=N1WTorLKL0uwLsU_" title="YouTube video player" frameborder="0" allow="accelerometer; autoplay; clipboard-write; encrypted-media; gyroscope; picture-in-picture; web-share" allowfullscreen></iframe>

## Bilibili

<iframe width="100%" height="468" src="//player.bilibili.com/player.html?bvid=BV1fK4y1s7Qf&p=1" scrolling="no" border="0" frameborder="no" framespacing="0" allowfullscreen="true"> </iframe>
---
title: Network Security | Thailand Cyber Top Talent 2025 junior [Qualifier]
published: 2025-09-03
description: CTF-Writeup THCTT 2025 junior [Qualifier] | Network Security kub pom :)
image: https://miro.medium.com/v2/resize:fit:1100/format:webp/1*bk_aSDegtilLL4x1O29XoA.png
tags: [Thailand Cyber Top Talent, network security, ctf, NCSA]
category: CTF-Writeup
draft: true
---

# Network Security | Thailand Cyber Top Talent 2025 Junior [Qualifier]

_by ShoIsMyName • Sep 2025_

![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*bk_aSDegtilLL4x1O29XoA.png)

หนีห่าว ว่อเจี้ยวโช วันนี้จะมาแสดงวิธีทำโจทย์ ของงาน cyber top talent 2025 หมวด network security กันนะครับ ส่วนหมวดอื่นๆผมจะคอยทยอยลงนะครับ พอดีช่วงนี้ติดเกม5555555555

## 1. Love Letter (100 points)      
![img](https://miro.medium.com/v2/resize:fit:640/format:webp/1*_uiC9un8tPxQpjyZhFO-Lw.png)

ไฟล์ที่เราได้มาจะมีไฟล์ .pcap มาหนึ่งไฟล์ โดยเราจะเริ่มดู log คร่าวๆกันก่อน
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*xfZUB40S1VEb-ot0fiHBqw.png)

จากที่เห็นก็ถือว่าไม่ได้เยอะอะไรมาก พอเลื่อนดู tcp udp stream ได้อยู่ แต่จุดที่เราสนใจจะอยู่ที่ `tcp.stream eq 4` เพราะมีการ communicate กันระหว่าง **MINECRAFT_CLIENT** กับ **MINECRAFT_SERVER**
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*vAfmCchB6kE0xLR-J1nPzw.png)

`tcp.stream eq 4`

เนื้อหาข้างในไฟล์ tcp stream จะเป็นแบบนี้
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*luISlRWQXw967WXwaGFjMw.png)

ซึ่งเราจะเห็น variable ชื่อว่า “data” ดูเหมือนว่าแต่ละ string ของข้อมูลจะถูกส่งเป็นช่วงๆ เพราะฉะนั้นเราจึงเอา strings มาต่อกัน เราก็จะได้

```
UEsDBBQAAAAIAKYAEls0JprpZwEAADUCAAAPAAAAbG92ZV9sZXR0ZXIudHh0RZFBb9swDIXv/hW89RIEbdpl3bGHASuw3gYMPdISFROVxECS4xlD//uenAC72AAfyffx6W0lL1yktt0wvNI4a2zEVM/ilCO5ibVQsEJzJc1VvZDNhd40iyscGi1Wot/Td3YTjdHcB00WfcWOs4pDd6C00gSPhq6LlBXCH4ldWMw8aSXH5SKeFm0T5pIkQxf07sT+IrnNINwPww/1XvLWqJnwqVd/iip1G62VT4I/50aW47qxrzbv6ZfRnJ2BgLTteu0uRsoC42ZkZ+kL5XYxZ3/jb3YS1MsmjmuDzytFCbjm94QZ7KGgaO96RSjyf/nEF6FzsX5KQC4LpRkx9ZFO2H2T4KwXsMeF17rbTo6A 7LEIcD3wsjVkT85SAheaxnkrdMemSWiR/mBg8IIJzadNuiYDrT+qh83PvvdmNLx3pysvMk5apAxDiHz6G+7HR/kqj1+Oz8eHY+Cjf+LDgf29+Cf3/E0+h39QSwECFAMUAAAACACmABJbNCaa6WcBAAA1AgAADwAAAAAAAAAAAAAAgAEAAAAAbG92ZV9sZXR0ZXIudHh0UEsFBgAAAAABAAEAPQAAAJQBAAAAAA==
```

จากนั้นเราเอาไป decode base64 ดู จะเห็นว่าคำนำหน้า output เป็น `PK` นั่นหมายความว่าข้อมูลนี้เป็น raw ที่สามารถแปลงกลับเป็นไฟล์ปกติได้
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*WYoxRdzmoNsb2qls7yJdWg.png)

จากนั้นเราจะใส่ unzip เข้าไปเพื่อ compile file ให้กลับเป็นรูปเดิม
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*87g6tIdCARNXKJ3MiTo8CA.png)

เราก็จะได้ flag ในที่สุด

> flag{f0b3e7e3568616fa6d4a22ad0ed4c89e}

## 2. Cipher Puzzle (200 points)
![img](https://miro.medium.com/v2/resize:fit:640/format:webp/1*1YUPQEr00sBj9Quc3i3keA.png)

ไฟล์ที่เราจะได้มาก็เหมือนกับข้อที่แล้ว มีไฟล์ .pcap แค่อันเดียว ไม่รอช้า ลากเข้า wireshark เลย!
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*4BAuKXFeHldSfGsXXhYOjw.png)

เอ๊ะแรกคือ log มีน้อย เอ๊ะสองคือมี tcp เยอะเหมือนข้อแรก ผมเลยมุ่งไปที่ tcp stream อันดับแรกเลย และก็บิงโก!!
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*O13PuU-PrSRs0H-objyLUw.png)

เพราะเราเจอข้อความที่เป็น hex และถูกส่ง string เป็นช่วงๆ เหมือนข้อ Love Letter คราวนี้เราก็พอจะเดาได้ว่าเราต้องทำอะไรต่อ เริ่มจากเอา strings มาต่อกัน

```
2504020b004d071c0e0a0305426d65210e00002c0c154e0e1c4d090b150a436b2747070c170b470704050a02014d0000081b05041c470208121d0608084108081d4d180112414d6b6401030c0615525f0b030f5f595d0258045a5e555d510c0f0008010a55525756595c580b5158106b
```

จากนั้นก็ hex decrypt เพื่อให้ cipher อยู่ในรูปปกติ แต่เหมือนว่ามันจะถูก xor ด้วย key อะไรบางอย่าง
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*K4dEVP5fEgsrPfDsSrmypw.png)

วิธีที่เราจะใช้คือ xor brute force ด้วย wordlist เริ่มจากโหลด output ที่ได้จากตอน hex decrypt มาก่อน (`.dat`)
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*IuBeqVrT4IAHr_Ga2RUnyg.png)

หน้าตาก็จะประมาณนี้แหละ

จากนั้นเราจะ brute force ด้วย python code สามารถใช้โค้ดด้านล่างนี้ได้เลย และ wordlist ที่ใช้จะเป็น rockyou.txt (จาก GitHub)

```python
def xor_bytes(data, key: bytes) -> bytes:  
    return bytes([b ^ key[i % len(key)] for i, b in enumerate(data)])  

# download cipher   
with open("download.dat", "rb") as f:  
    ciphertext = f.read()

# import wordlist   
with open("rockyou.txt", "r", encoding="utf-8", errors="ignore") as f:  
    keys = [line.strip().encode() for line in f]  

for key in keys:  
    plaintext = xor_bytes(ciphertext, key)  
    # filter the answer (ASCII)  
    if all(32 <= c < 127 or c in (10, 13) for c in plaintext[:200]):  
        print(f"[KEY: {key.decode(errors='ignore')}] => {plaintext[:200]}")
```
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*bD_2s_olfC5UuVNPf1a1Xw.png)

หรือจะเอาไป xor โต้งๆอีกทีใน cyberchef ก็ได้
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*ntqORpY2mcJE3DqUWRj_Qw.png)

now we got the flag!!!

> flag{50fba860c6c53436cbaffe8391619e67}

## Thank you for reading kub pom ❤
![img](https://miro.medium.com/v2/resize:fit:1100/format:webp/1*qbnyB8KCc2JRwb_ht4B59w.png)

**Tags:** Thctt2025, CTF, CTF Writeup, Network Security

