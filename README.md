<p align="center">
<img src="./HSTU_Logo.png" alt="HSTU Logo" width="150">
</p>
<h2 align="center"><strong>Hajee Mohammad Danesh Science And Technology University</strong></h2>
<h3 align="center">Dinajpur-5200</h3>


<h2 align="center" style="color:#16a085;"><strong> Course Information</strong></h2>

<p align="center">
  <strong>Course Title:</strong> Mathematical Analysis for Computer Science  
  <br>
  <strong>Course Code:</strong> CSE 361
</p>

---

<h2 align="center" style="color:#2980b9;"><strong> Algorithm Name</strong></h2>

<h1 align="center" style="color:#8e44ad;"><strong>  Position Swap Cipher </strong></h1>

---

<h2 align="center" style="color:#16a085;"><strong> Submitted By</strong></h2>

<p align="center">
  <strong>Name: Raisa Islam Fariha </strong> 
  <br>
  <strong>Student ID:</strong> 2102018  
  <br>
  <strong>Level:</strong> 3  
  <br>
  <strong>Semester:</strong> II  
  <br>
  <strong>Department:</strong> Computer Science and Engineering  
</p>

---
<h2 align="center" style="color:#16a085;"><strong> Submitted To</strong></h2>

<p align="center">
  <strong>Name:</strong> Pankaj Bhowmik  
  <br>
  <strong>Designation:</strong> Lecturer  
  <br>
  <strong>Department:</strong> Computer Science and Engineering  
</p>

---

## 🧾 Introduction

Cryptography plays a crucial role in securing digital communication. While modern encryption algorithms are complex and mathematically intensive, learning begins with understanding basic principles. The **Position Swap Cipher** is a simple, custom-designed encryption method created to demonstrate core cryptographic concepts such as **character manipulation**, **data transformation**, and **symmetry in encryption and decryption**.
## 🔧 Core Techniques Used

The **Position Swap Cipher** algorithm combines two fundamental techniques:

1. **Swapping Adjacent Characters**  
   This step alters the structure of the input message by swapping every two adjacent characters.
   For example:
   
   Input: HELLO
   
   Step: Swap 0↔1, 2↔3 → EHLLO
   
2. **Caesar Shift (+1)**  
After swapping, each character is shifted forward by 1 in its ASCII value to further obscure the content.  
For example:  
'A' → 'B', '1' → '2', 'Z' → '['

---
## 🛠️ Encryption Process

The encryption process in the **Position Swap Cipher** involves two simple steps:

### 1. Swap Adjacent Characters  
Each pair of characters in the plaintext is swapped to alter the original structure.

**Example**:  
```text
Given: PLAINTEXT
Step 1: Swap adjacent characters
P L A I N T E X T
↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓ ↓
L P I A T N X E T (swap 0↔1, 2↔3, 4↔5, 6↔7)

### 2. Apply Caesar Shift (+1)  
Every character in the swapped string is shifted forward by 1 in its ASCII value.

**Example**:  
L → M
P → Q
I → J
A → B
T → U
N → O
X → Y
E → F
T → U

🔐 **Final Ciphertext**: `MQJBUOYFU`
```
## 🔓 Decryption Algorithm 

The **Position Swap Cipher** decryption process reverses the steps applied during encryption. It ensures that the original plaintext is recovered accurately from the ciphertext.

---

### 🔄 Step-by-Step Process:

#### **Step 1: Caesar Shift (−1)**  
Each character in the ciphertext is shifted backward by 1 in its ASCII value to undo the Caesar shift applied during encryption.

#### 🔍 Example:
Ciphertext: M Q J B U O Y F U
Shift −1 → L P I A T N X E T

After this step, the intermediate string is:  
**LPIATNXET**

---

#### **Step 2: Swap Adjacent Characters Back**  
Now, the algorithm swaps adjacent characters again to undo the structural rearrangement done earlier.

#### 🔁 Swap index pairs: 0↔1, 2↔3, 4↔5, 6↔7

Input: L P I A T N X E T
Swap → P L A I N T E X T

✅ **Final Output (Plaintext)**: `PLAINTEXT`

---

## 🔑 Key Used:
- Fixed Caesar shift: **+1**
- Simple swap: no additional key needed.

---

# Source Code : (Python)

```text
def encrypt(text):
    # Step 1: Swap adjacent characters
    text = list(text)
    for i in range(0, len(text) - 1, 2):
        text[i], text[i + 1] = text[i + 1], text[i]
    
    # Step 2: Caesar shift (+1)
    encrypted = ""
    for ch in text:
        encrypted += chr((ord(ch) + 1) % 256)
    return encrypted

def decrypt(cipher):
    # Step 1: Caesar shift (−1)
    temp = ""
    for ch in cipher:
        temp += chr((ord(ch) - 1) % 256)

    # Step 2: Swap adjacent characters back
    temp = list(temp)
    for i in range(0, len(temp) - 1, 2):
        temp[i], temp[i + 1] = temp[i + 1], temp[i]
    return ''.join(temp)

# Test
plaintext = "PLAINTEXT"
ciphertext = encrypt(plaintext)
decrypted = decrypt(ciphertext)

print("Plaintext:", plaintext)
print("Encrypted:", ciphertext)
print("Decrypted:", decrypted)

```
