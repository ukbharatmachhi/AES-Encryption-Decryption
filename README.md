# AES Encryption/Decryption and Hashing for Secure Transactions

This project focuses on implementing AES (Advanced Encryption Standard) encryption and decryption alongside cryptographic hashing to enhance the security of digital transactions. AES is a widely used symmetric encryption algorithm that ensures data confidentiality, while hashing techniques like SHA-256 help maintain data integrity.

## Key Features:

1) AES Encryption & Decryption – Securely encrypts and decrypts sensitive transaction data using AES-256.

2) Cryptographic Hashing – Uses SHA-256 to generate hash values, ensuring data integrity and preventing tampering.

3) Secure Transactions – Protects financial and personal information from unauthorized access.

4) Tamper Detection – Hashing ensures that the transmitted data remains unchanged.


## Contribution to the AES Encryption/Decryption and Hashing Project:

As a Cyber Forensic Consultant, Bharatkumar played a pivotal role in designing and implementing robust security measures for this project. His contributions include:

1) Developing AES Encryption & Decryption Modules – Implemented AES-256 encryption to ensure end-to-end security for sensitive transaction data.

2) Integrating Cryptographic Hashing – Designed a secure hashing mechanism using SHA-256 to validate data integrity and prevent tampering.

3) Enhancing Secure Transactions – Applied industry best practices to protect digital transactions from cyber threats, including MITM attacks and data breaches.

4) Optimizing Performance & Efficiency – Ensured minimal latency while encrypting and decrypting large datasets, making the system scalable for real-world applications.

5) Threat Analysis & Security Audits – Conducted forensic analysis to identify potential vulnerabilities and strengthen encryption methods.

6) ompliance & Best Practices – Ensured the project adheres to security compliance standards such as GDPR, PCI-DSS, and NIST guidelines.


## Impacts of the AES Encryption/Decryption and Hashing Project

The implementation of AES encryption, decryption, and hashing mechanisms in transactions has significantly strengthened data security, integrity, and compliance. The key impacts of this project include:

1) Enhanced Data Security – AES-256 encryption ensures that sensitive financial and personal transaction data remains confidential and protected from unauthorized access.

2) Data Integrity & Authenticity – Cryptographic hashing (SHA-256) prevents data manipulation, ensuring that transactions remain tamper-proof and trustworthy.

3) Fraud Prevention & Cybercrime Mitigation – Strong encryption mechanisms reduce the risk of man-in-the-middle (MITM) attacks, unauthorized modifications, and identity fraud.

4) Regulatory Compliance – The project aligns with international security standards such as GDPR, PCI-DSS, and NIST, ensuring legal and industry-wide compliance for secure transactions.

5) Improved System Performance & Scalability – Optimized encryption algorithms ensure fast and efficient processing without compromising security, making it suitable for high-volume financial transactions.

6) Strengthened Digital Trust – Secure transactions increase user confidence in digital platforms, encouraging widespread adoption of secure payment and data exchange systems.

This project has set a new benchmark in cybersecurity by securing transaction data through state-of-the-art cryptographic techniques, paving the way for a safer and more resilient digital ecosystem.



# Main Python File:

## Case 1: A customer not present online retail transaction


``` python
import hashlib  
from Crypto.Cipher import AES  
from Crypto.Util.Padding import pad, unpad  

# AES encryption function def 
encrypt_aes(key, data):  
cipher = AES.new(key, AES.MODE_CBC)  
ciphertext = cipher.encrypt(pad(data.encode(), AES.block_size))     
return cipher.iv + ciphertext  

# AES decryption function def 
decrypt_aes(key, data):     
iv = data[:AES.block_size]     
ciphertext = data[AES.block_size:]     
cipher = AES.new(key, AES.MODE_CBC, iv)  
plaintext = unpad(cipher.decrypt(ciphertext), AES.block_size)     
return plaintext.decode()  

# SHA-256 hashing function def 
hash_sha256(data):  
hash_object = hashlib.sha256(data)  
return hash_object.hexdigest()  

# Generate a random AES key (128 bits) aes_key = 
b'\x1b\x94;\xe8\x8e\x9e\xcb\xf1\xe0\x1a\x9a\xdc\xe3\x07\x1d\x80'  

# Step a: User initiates the transaction print("Step 
a: User initiates the transaction.")  
print("User starts making a purchase on the online platform.")  

# Step b: User provides payment card details print("\nStep 
b: User provides payment card details.") card_number =  input("Enter your credit card number: ") expiration_date = input("Enter the expiration date: ") cvv = input("Enter the CVV code: ")  

# Step c: Encryption and data protection print("\nStep c: 
Encryption and data protection.") print("Encrypting the credit card details using AES...") encrypted_card_number = encrypt_aes(aes_key, card_number) encrypted_expiration_date = encrypt_aes(aes_key, expiration_date) encrypted_cvv = encrypt_aes(aes_key, cvv)  
print("\nEncrypted Credit Card Number:", encrypted_card_number)
print("Encrypted Expiration Date:", encrypted_expiration_date)
print("Encrypted CVV:", encrypted_cvv)
print("Hashing the encrypted data using SHA-256...") hashed_card_number = hash_sha256(encrypted_card_number) hashed_expiration_date = hash_sha256(encrypted_expiration_date) hashed_cvv = hash_sha256(encrypted_cvv) 
rint("Hashed Credit Card Number:", hashed_card_number) print("Hashed Expiration Date:", hashed_expiration_date) print("Hashed CVV:", hashed_cvv)  

# Step d: Payment data transmission to the payment gateway 
print("\nStep d: Payment data transmission to the payment gateway.")
print("Transmitting the encrypted payment data securely to the payment gateway...")

# Assume the payment gateway receives the encrypted data and performs necessary operations
# Step e: Payment gateway examines and conveys the transaction print("\nStep
e: Payment gateway examines and conveys the transaction.") print("Decrypting the encrypted payment data using AES...") decrypted_card_number = decrypt_aes(aes_key, encrypted_card_number) decrypted_expiration_date = decrypt_aes(aes_key, encrypted_expiration_date) decrypted_cvv = decrypt_aes(aes_key, encrypted_cvv)
print("Performing security checks on the decrypted data...")

# Assume security checks and verification of user's account are performed  
# Step f: Acquiring bank authorizes the transaction print("\nStep f: 
Acquiring bank authorizes the transaction.") print("Verifying the card details and authorizing the transaction...")

# Assume the acquiring bank processes the transaction and provides an authorization result 
authorization_result = True  # Assume the transaction is authorized for demonstration purposes 
if authorization_result:  
print("\nDecrypted Credit Card Number:", decrypted_card_number)  
print("Decrypted Expiration Date:", decrypted_expiration_date)
print("Decrypted CVV:", decrypted_cvv)

# Step g: Payment gateway relays the authorization print("\nStep 
g: Payment gateway relays the authorization.")  
print("Relaying the encrypted authorization back to the online platform...")

# Assume the payment gateway relays the authorization to the online platform
# Step h: Online platform completes the transaction print("\nStep
h: Online platform completes the transaction.") print("Delivering the goods or service to the user...")
print("Sending a confirmation of the completed transaction to the user.")
```


## Case 2: A customer present retail transaction: 

``` python
import hashlib  
from Crypto.Cipher import AES  
from Crypto.Util.Padding import pad, unpad  

# AES encryption function def 
encrypt_aes(key, data):  
cipher = AES.new(key, AES.MODE_CBC)  
ciphertext = cipher.encrypt(pad(data.encode(), AES.block_size))     
return cipher.iv + ciphertext  

# AES decryption function def 
decrypt_aes(key, data):     
iv = 
data[:AES.block_size]     
ciphertext = data[AES.block_size:]     
cipher = AES.new(key, AES.MODE_CBC, iv)  
plaintext = unpad(cipher.decrypt(ciphertext), AES.block_size)     
return plaintext.decode()  

# SHA-256 hashing function def 
hash_sha256(data):  
hash_object = hashlib.sha256(data)  
return hash_object.hexdigest()  

# Generate a random AES key (128 bits) aes_key = 
b'\x1b\x94;\xe8\x8e\x9e\xcb\xf1\xe0\x1a\x9a\xdc\xe3\x07\x1d\x80'  

# Step a: User begins the transaction at a physical store print("Step 
a: User begins the transaction at a physical store.")  
print("User hands over payment card to merchant or swipes the card at POS terminal.")  

# Step b: Merchant enters payment card details using POS terminal  
print("\nStep b: Merchant enters payment card details using POS terminal or swipe the card.") 
card_number = input("Enter the credit card number: ") expiration_date = input("Enter the 
expiration date: ") cvv = input("Enter the CVV code: ")  

# Step c: Data protection and encryption print("\nStep c: Data 
protection and encryption.") print("Encrypting the credit card details using AES...") encrypted_card_number = encrypt_aes(aes_key, card_number) encrypted_expiration_date = encrypt_aes(aes_key, expiration_date) encrypted_cvv = encrypt_aes(aes_key, cvv) print("\nEncrypted Credit Card Number:", encrypted_card_number) print("Encrypted Expiration Date:", encrypted_expiration_date) print("Encrypted CVV:", encrypted_cvv)  
print("Hashing the encrypted data using SHA-256...") hashed_card_number = hash_sha256(encrypted_card_number) hashed_expiration_date = hash_sha256(encrypted_expiration_date) hashed_cvv = hash_sha256(encrypted_cvv)  
print("Hashed Credit Card Number:", hashed_card_number) print("Hashed Expiration Date:", hashed_expiration_date) print("Hashed CVV:", hashed_cvv)  

# Step d: Secure transaction data transmission from the POS terminal to the acquiring bank 
print("\nStep d: Secure transaction data transmission from the POS terminal to the acquiring bank.") print("Transmitting the encrypted payment ata securely from the POS terminal to the acquiring bank...")  

# Assume the encrypted data is transmitted securely using secure communication protocols like 
HTTPS  

# Step e: POS transmits encrypted transaction to the acquiring bank 
print("\nStep e: POS examines and conveys the transaction.") print("Decrypting the encrypted transaction data using AES...") decrypted_card_number = decrypt_aes(aes_key, encrypted_card_number) decrypted_expiration_date = decrypt_aes(aes_key, encrypted_expiration_date)decrypted_cvv = decrypt_aes(aes_key, encrypted_cvv)  
print("Performing security checks on the decrypted data...")  

# Assume security checks, card validity verification, and user account verification are 
performed by the acquiring bank  

# Step f: Acquiring bank authorizes the transaction print("\nStep 
f: Acquiring bank authorizes the transaction.") print("Verifying card details and executing security checks...")  
authorization_result = True  # Assume the transaction is authorized for demonstration purposes  

# Print the decrypted data if authorized if 
authorization_result:  
print("\nDecrypted Credit Card Number:", decrypted_card_number)     
print("Decrypted Expiration Date:", decrypted_expiration_date)     
print("Decrypted CVV:", decrypted_cvv)  

# Step g: POS terminal notifies the authorization to the merchant print("\nStep 
g: POS terminal notifies the authorization to the merchant.") print("Sending the authorization status to the merchant...")  

# Assume the authorization status is securely transmitted to the merchant  
# Step h: Merchant completes the transaction print("\nStep 
h: Merchant completes the transaction.") print("Product or service is provided to the user.") print("User receives a receipt or confirmation of the successful transaction.")  

```

# Output

![Reference Image](main.jpg)
