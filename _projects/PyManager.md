---
layout: post
title: PyManager
description: Military Grade Python Password Manager
year: 2024
tags:
  - Python
  - Security
---

        ____        __  ___
       / __ \__  __/  |/  /___ _____  ____ _____ ____  _____
      / /_/ / / / / /|_/ / __ `/ __ \/ __ `/ __ `/ _ \/ ___/
     / ____/ /_/ / /  / / /_/ / / / / /_/ / /_/ /  __/ /
    /_/    \__, /_/  /_/\__,_/_/ /_/\__,_/\__, /\___/_/
          /____/                         /____/


![](https://img.shields.io/badge/SQLite-07405E?style=for-the-badge&logo=sqlite&logoColor=white)
![](https://img.shields.io/badge/Python-14354C?style=for-the-badge&logo=python&logoColor=white)

[PyManager](https://github.com/judz5/PyManager) is a secure and easy to use password managment application written in Python. Passwords are encypted using AES-256, with Password-Based Key Derivation for ultimate security. Data is stored with sqlite for ease of setup and use.

## Setup

1. **Clone the repository:**

   ```bash
   git clone https://github.com/judz5/PyManager
   cd PyManager
   ```
2. **Intstall required librarys**

   ```bash
   pip install -r requirements.txt
   ```
3. **Run the Main Script**

   ```bash
   python3 main_control.py
   ```

*If its your first time running the application, be sure to choose option 5 to configure the database before attempting to add any accounts.*

---

https://www.bluespace.tech/blog/evolution-of-password-manager/second-generation-password-manager.html

https://cryptobook.nakov.com/symmetric-key-ciphers/aes-encrypt-decrypt-examples
