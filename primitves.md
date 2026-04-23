

---
title: primitves  
tags:
  - "#programming"
  - "#goglang"
  - "#primitves"
author:
  - yzpk  
  - ai  
description:
---
```golang
package main

import "fmt"

func main() {
	a := 10
	b := 3
	fmt.Println (a & b)
	fmt.Println (a | b)
	fmt.Println (a ^ b)
	fmt.Println (a &^ b)
}
```

ဒီ Go code ကတော့ **Bitwise Operators** တွေကို အသုံးပြုပုံကို ပြထားတာဖြစ်ပါတယ်။ Bitwise ဆိုတာ ကိန်းဂဏန်းတွေကို Binary (0 နဲ့ 1) အဖြစ်ပြောင်းလဲပြီး တစ်လုံးချင်းစီ တိုက်စစ်တွက်ချက်တာကို ဆိုလိုပါတယ်။

နားလည်လွယ်အောင် a=10 နဲ့ b=3 ကို Binary အဖြစ် အရင်ပြောင်းကြည့်ရအောင်။

- **10** ကို Binary ပြောင်းရင်: `1010`
    
- **3** ကို Binary ပြောင်းရင်: `0011`
    

---

### ကုဒ်တစ်ခုချင်းစီရဲ့ ရှင်းလင်းချက်

**1. `fmt.Println(a & b)` (Bitwise AND)** နှစ်ဖက်စလုံး `1` ဖြစ်မှသာ `1` ရပါမယ်။

1010  (10)
 & 0011 (3)     => 0010 => ရလဒ်က 2 ဖြစ်ပါတယ်။
 
 ---

**2. `fmt.Println(a | b)` (Bitwise OR)** အနည်းဆုံး တစ်ဖက်က 1 ဖြစ်ရင် 1 ရပါမယ်။
Plaintext

  1010  (10)
  | 0011 (3)       =>1011  => ရလဒ်က 11 ဖြစ်ပါတယ်။
  
  ----
  
3. fmt.Println(a ^ b) (Bitwise XOR) မတူရင် 1 ရမယ်၊ တူရင် (ဥပမာ 0,0 သို့မဟုတ် 1,1) 0 ရပါမယ်။
Plaintext

  1010  (10)
^ 0011  (3)
-------
  1001  => ရလဒ်က 9 ဖြစ်ပါတယ်။

4. fmt.Println(a &^ b) (Bitwise AND NOT / Bit Clear) ဒါက Go ရဲ့ ထူးခြားတဲ့ operator ပါ။ ဒုတိယကိန်း (b) မှာ 1 ဖြစ်နေတဲ့ နေရာတွေကို ပထမကိန်း (a) မှာ သွားပြီး 0 (Clear) လုပ်ပစ်တာပါ။

    b မှာ 1 ရှိတဲ့ နေရာဆိုရင် ရလဒ်က အမြဲ 0 ဖြစ်မယ်။

    b မှာ 0 ရှိတဲ့ နေရာဆိုရင်တော့ a ရဲ့ မူလတန်ဖိုးအတိုင်း ယူပါမယ်။

Plaintext

   1010  (10)
&^ 0011  (3)
--------
   1000  => ရလဒ်က 8 ဖြစ်ပါတယ်။

အနှစ်ချုပ် ရလဒ်များ

ဒီ Program ကို Run လိုက်ရင် အောက်ပါအတိုင်း ထွက်လာပါလိမ့်မယ်။

    2

    11

    9

    8
---
```golang
package main

import "fmt"

func main() {
	a := 8              // 2^3
	fmt.Println(a << 3) // 2^3 * 2^3
	fmt.Println(a >> 3) // 2^3 / 2^3
}
```
## 1️⃣ `a := 8`  

- `8` ကို binary နဲ့ရေးရင်
    

- `8 = 1000₂ = 2³`
    

---

## 2️⃣ `a << 3` (Left Shift)

`fmt.Println(a << 3)`

- `<<` ဆိုတာ **left shift** ဖြစ်ပြီး  
    👉 `2ⁿ` နဲ့မြှောက်တာနဲ့ တူပါတယ်
    
- `a << 3` ဆိုတာ
    

- `8 × 2³ = 8 × 8 = 64`
    

### Binary အနေနဲ့ကြည့်ရင်

`8  = 00001000 <<3 ----------------      01000000  = 64`

✅ Output:

`64`

---

## 3️⃣ `a >> 3` (Right Shift)

`fmt.Println(a >> 3)`

- `>>` ဆိုတာ **right shift** ဖြစ်ပြီး  
    👉 `2ⁿ` နဲ့စားတာနဲ့ တူပါတယ်
    
- `a >> 3` ဆိုတာ
    

- `8 ÷ 2³ = 8 ÷ 8 = 1`
    

### Binary အနေနဲ့ကြည့်ရင်

`8  = 00001000 >>3 ----------------      00000001 = 1`

✅ Output:

`1`

---

## 🔑 အကျဉ်းချုပ်

|Expression|အဓိပ္ပါယ်|Result|
|---|---|---|
|`a << n`|`a × 2ⁿ`|64|
|`a >> n`|`a ÷ 2ⁿ`|1|

ဒီလို **bit shifting** ကို

- performance မြန်တဲ့ multiplication / division
    
- low-level programming
    
- flags & bitmask တွေမှာ အရမ်းအသုံးများပါတယ်။
    

---
```golang
package main

import "fmt"

func main() {
	a := 10.2
	b := 3.7
	fmt.Println(a + b)
	fmt.Println(a - b)
	fmt.Println(a * b)
	fmt.Println(a / b)
}
```

## 📌 Code ရဲ့ အလုပ်လုပ်ပုံ (ရှင်းပြချက်)

### `a` နဲ့ `b`

- `a := 10.2`
    
- `b := 3.7`
    
- ဒါတွေက **float64** type တွေပါ (Go မှာ default)
    

---

### Arithmetic Operations

|Code|အဓိပ္ပါယ်|Result|
|---|---|---|
|`a + b`|ပေါင်း|13.9|
|`a - b`|နုတ်|6.5|
|`a * b`|မြှောက်|37.74|
|`a / b`|စား|2.756756...|

Output:

`13.9 6.5 37.74 2.7567567567567566`

---
```golang
package main

import "fmt"

func main() {
	var n complex64 = 1 + 2i
	fmt.Printf("%v, %T\n", n, n)
}
```
---

`var n complex64 = 1 + 2i`

- `n` ဆိုတဲ့ variable ကို ထားပါတယ်
    
- Type က `complex64` (complex number)
    
- `1 + 2i` ဆိုတာ
    
    - **Real part = 1**
        
    - **Imaginary part = 2i**
        

📌 `complex64` ဆိုတာ

- real part → `float32`
    
- imaginary part → `float32`
    

---

`fmt.Printf("%v, %T\n", n, n)`

- `Printf` ကို format string နဲ့အသုံးပြုထားပါတယ်
    

Format specifiers:

- `%v` → variable ရဲ့ **တန်ဖိုး**
    
- `%T` → variable ရဲ့ **type**
    

ဒါကြောင့်

- `%v` က `1+2i` ကိုပြမယ်
    
- `%T` က `complex64` ကိုပြမယ်
    

---

### 🔍 Output

`(1+2i), complex64`

---

### အကျဉ်းချုပ်

ဒီ program က

- complex number တစ်ခု (`1 + 2i`) ကို 선언 လုပ်တယ်
    
- အဲ့ဒီတန်ဖိုးနဲ့ type ကို screen ပေါ်မှာ ပြပါတယ်
---
```golang
package main

import "fmt"

func main() {
	var n complex64 = 2i
	fmt.Printf("%v, %T\n", n, n)
}
```
ဒီ code ကလည်း အရင် code နဲ့ ဆင်တူပါတယ်။ ကွာခြားတာကို အလေးထားပြီးရှင်းပြပါမယ် 👇

`var n complex64 = 2i`

### 🔹 ဒီလိုရေးထားတာ ဘာကိုဆိုလိုလဲ?

- `2i` ဆိုတာ **imaginary part တစ်ခုတည်းရှိတဲ့ complex number**
    
- Go မှာ
    

- 2i ဆိုတာ `2i ≡ 0 + 2i` လိုမျိုး ပေါင်းထားတာနဲ့ တူတယ်
    
    လို့ အဓိပ္ပါယ်ရပါတယ်
    

အဲ့ဒီကြောင့်

- **Real part = 0**
    
- **Imaginary part = 2**
    

---

`fmt.Printf("%v, %T\n", n, n)`

- `%v` → တန်ဖိုးကိုပြ
    
- `%T` → type ကိုပြ
    

---

### 🔍 Output

`(0+2i), complex64`

---

### 📌 မှတ်သားရမယ့်အချက်

- Go မှာ complex number ကို
    
    - `1 + 2i`
        
    - `2i`
        
    - `complex(1, 2)`  
        ဆိုပြီးရေးလို့ရပါတယ်
        
- `2i` ကိုရေးရင် **real part ကို 0 အလိုအလျောက်ထားပေးပါတယ်**
    

---

### အကျဉ်းချုပ်

ဒီ program က

- imaginary part ပဲရှိတဲ့ complex number (`0+2i`) ကို 선언 လုပ်တယ်
    
- အဲ့ဒီတန်ဖိုးနဲ့ type ကို print ထုတ်ပါတယ်

