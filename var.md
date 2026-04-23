

---
title: golang pdf
tags:
  - "#goglang"
  - "#programming"
author:
  - ai
  - yzpk
created:
description:
---


1.var keyword ဖြင့် ကြေညာခြင်း

Data type ကို တိတိကျကျ သတ်မှတ်ပေးနိုင်သည်။

//data type ကို သတ်မှတ်ပြီး ကြေညာခြင်း
var name string = "\Aung Aung"

//data type မပါပဲ ကြေညာခြင်း ( go က တန်ဖိုးကို ကြည့်၍ type ကို အလိုအလျောက် သတ်မှတ်ပေးသည်)
var age = 25

//တန်ဖိုးမထည့်ပဲ ကြေညာခြင်း ( zero value ဖြစ်သည့် "" သို့မဟုတ် 0 ကို ရရှိမည်)
var address string

2.Short Variable Declaration (:=)

ဤနည်းလမ်းသည် functionများအတွင်းတွင် အသုံးအများဆုံးဖြစ်ပြီး var keyword နှင့် type ကို ရေးရန်မလိုပဲ variable ကို အတို ကြေညာနိုင်သည်။

---
## Printf format specifier အသုံးများ 🔧

|Specifier|အဓိပ္ပါယ်|
|---|---|
|`%s`|string|
|`%d`|int|
|`%f`|float|
|`%.2f`|float (decimal 2 လုံး)|
|`%v`|any value|
|`%T`|type|

---------
##### You said:

```golang
package main

import (

"fmt"

"sort"

)

func main() {

ages := map[string]int {

"Aung Aung": 25,

"Ma Ma" : 30,

}

fmt.Println("Inital Map:", ages)

delete(ages, "Ma Ma")

fmt.Println("After delete:", ages)

val, ok := ages["Kyaw Kyaw"]

if ok {

fmt.Println("Kyaw Kyaw's age is", val)

} else {

fmt.Println("Kyaw Kyaw not found.")

}

testScores := map[string]int{

"Charlie" : 88,

"Alice" : 95,

"Bob" : 72,

}

fmt.Println("\nUnordered Iteration:")

for name, score := range testScores {

fmt.Printf ("Name: %s, Score: %d", name, score)

}

var names [] string

for name := range testScores {

names = append(names, name)

}

sort.Strings(names)

fmt.Println("Sorted Iteration:")

for _, name := range names {

fmt.Printf("Name: %s, Score: %d", name, testScores[name])

}

}
```
အထက်ပါ ကုဒ်ကို ရှင်းပြပါ

ကောင်းပါပြီ—ဒီ Go code ကို **အပိုင်းလိုက် လွယ်လွယ်နားလည်အောင်** ရှင်းပြမယ်နော် 😊  
(နောက်ဆုံးမှာ သင်နားလည်မှု စစ်တဲ့ မေးခွန်းလေး ၁ ခု ထားမယ်)

---

## 1️⃣ Package နဲ့ Import

`package main`

- Program ရဲ့ entry point ဖြစ်တဲ့ **main package** ပါ။
    

`import ( 	"fmt" 	"sort" )`

- `fmt` → output (print) ပြဖို့
    
- `sort` → string slice ကို စီဖို့
    

---

## 2️⃣ main function

`func main() {`

Program စတင် run လုပ်တဲ့ function ဖြစ်ပါတယ်။

---

## 3️⃣ Map 선언 & အသုံးပြုခြင်း

`ages := map[string]int { 	"Aung Aung": 25, 	"Ma Ma" : 30, }`

- `map[string]int`  
    👉 **key = string**, **value = int**
    
- လူနာမည် → အသက် ကို သိမ်းထားတဲ့ map
    

`fmt.Println("Inital Map:", ages)`

- map ကို print ထုတ်ပြပါတယ်
    

---

## 4️⃣ Map ထဲက data ဖျက်ခြင်း

`delete(ages, "Ma Ma")`

- `"Ma Ma"` key ကို map ထဲက **ဖျက်**လိုက်တာပါ
    

`fmt.Println("After delete:", ages)`

- ဖျက်ပြီးနောက် map ကို ပြန်ပြပါတယ်
    

---

## 5️⃣ Map ထဲမှာ key ရှိ/မရှိ စစ်ခြင်း

`val, ok := ages["Kyaw Kyaw"]`

- `val` → value
    
- `ok` → key ရှိရင် `true`, မရှိရင် `false`
    

`if ok { 	fmt.Println("Kyaw Kyaw's age is", val) } else { 	fmt.Println("Kyaw Kyaw not found.") }`

- `"Kyaw Kyaw"` မရှိလို့ else ဘက်ကို ဝင်ပါတယ်
    

---

## 6️⃣ နောက်ထပ် Map တစ်ခု (testScores)

`testScores := map[string]int{ 	"Charlie" : 88, 	"Alice" : 95, 	"Bob" : 72, }`

- ကျောင်းသားအမည် → အမှတ်
    

---

## 7️⃣ Map ကို တိုက်ရိုက် loop လုပ်ခြင်း (Unordered)

`for name, score := range testScores { 	fmt.Printf ("Name: %s, Score: %d", name, score) }`

⚠️ **အရေးကြီး**

- Go map တွေဟာ **အစဉ်လိုက်မဟုတ်**
    
- run တိုင်း order မတူနိုင်
    

---

## 8️⃣ Sorted iteration (အစဉ်လိုက် ပြချင်ရင်)

### (1) key တွေကို slice ထဲ ထည့်

`var names []string for name := range testScores { 	names = append(names, name) }`

### (2) string slice ကို sort

`sort.Strings(names)`

### (3) စီထားတဲ့ key တွေနဲ့ map ကို ပြန်ဖတ်

`for _, name := range names { 	fmt.Printf("Name: %s, Score: %d", name, testScores[name]) }`

👉 ဒီနည်းနဲ့ **Alphabetical order** နဲ့ output ထွက်လာပါမယ်

---

## ✨ အကျဉ်းချုပ် (မှတ်ထားရမယ့်အချက်)

- `map` = key/value storage
    
- `delete(map, key)` → key ဖျက်
    
- `val, ok := map[key]` → key ရှိ/မရှိ စစ်
    
- Go map iteration = **unordered**
    
- Sort ချင်ရင် → key တွေကို slice ထဲထည့်ပြီး sort
    

---

### ❓ နားလည်မှု စစ်မေးခွန်း (၁ ခု)

Go မှာ map ကို `range` နဲ့ loop လုပ်ရင်  
**ဘာကြောင့် output order မသေချာတာလဲ?**

သင့်အမြင်ကို တစ်ကြောင်းလောက် ပြောကြည့်ပါ 😊

  

---
```golang
package main

import "fmt"

//Person အမည်ဖြင့် custom data type အသစ် တစ်ခု တည်ဆောက်ခြင်း
type Person struct {
	FirstName string
	LastName string
	Age     int
}

func main() {
	//Person struct မှ variable တစ်ခု တည်ဆောက်ခြင်း
		p1 := Person {
			FirstName : "Aung",
			LastName: "Kyaw",
			Age : 30,
			}
		fmt.Println("Person 1:", p1)
		fmt.Println("First Name:", p1.FirstName)
	p1.Age = 31
	fmt.Println("Updated Age:", p1.Age)
}
```

