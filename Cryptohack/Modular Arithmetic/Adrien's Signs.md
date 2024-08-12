## Description

![image](https://github.com/user-attachments/assets/2be7d411-b6b0-45d0-b027-a1900c476a79)

https://cryptohack.org/static/challenges/source_734d7e14251f950935f83d228f8694ab.py

https://cryptohack.org/static/challenges/output_80fc6398d2fd9f272186d0af510323f9.txt

## Solve

a = 288260533169915

p = 1007621497415251

def descrypt_flag(hehe):

    plaintext = []
    
    for i in hehe:
    
        if pow(i, (p - 1) // 2, p) == 1:
        
            plaintext.append('1')
            
        else:
        
            plaintext.append('0')
            
    plaintext = ''.join(plaintext)
    
    reversed(plaintext)
    
    plaintext = ''.join([chr(int(plaintext[i:i + 8], 2)) for i in range(0, len(plaintext), 8)])
   
    return plaintext

hehe = [...]

print(descrypt_flag(hehe))

- Flag :

`
crypto{p4tterns_1n_re5idu3s}
`
