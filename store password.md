## 安全储存密码

![Image description](https://github.com/yzyolala/OOD/blob/main/images/Screenshot%202023-11-21%20at%2002.23.26.png?raw=true)
![Image description](https://github.com/yzyolala/OOD/blob/main/images/Screenshot%202023-11-21%20at%2002.23.37.png?raw=true)
![Image description](https://github.com/yzyolala/OOD/blob/main/images/Screenshot%202023-11-21%20at%2002.23.53.png?raw=true)
![Image description](https://github.com/yzyolala/OOD/blob/main/images/Screenshot%202023-11-21%20at%2002.24.12.png?raw=true)

第一张图可能展示了如何在数据库中安全存储密码。通常，这涉及到以下几个步骤：

用户密码：用户创建的原始密码。
散列算法：使用散列函数（如SHA-256）来处理密码。
散列后的密码：原始密码经过散列处理后生成的散列值，通常是一串看似随机的字符，存储于数据库中。
第二张图可能展示了不同的散列算法速度对比，如MD5和SHA-1（通常较快，但不够安全）与bcrypt（较慢，但更安全）。

第三张图可能说明了加盐散列过程，其中“盐”是一个随机生成的字符串，与用户密码组合后一起进行散列，这样即便两个用户相同的密码，由于盐不同，其结果也会不同，增加了密码的安全性。

第四张图可能描绘了验证过程，其中用户提供的密码和盐一起再次被散列，然后与数据库中存储的散列值进行比较，以验证用户的密码是否正确。

这些步骤是密码存储安全性的基本原则，目的是保护用户的密码即使在数据库遭到未授权访问时也不容易被破解。
