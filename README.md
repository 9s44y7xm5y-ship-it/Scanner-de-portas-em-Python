# Scanner-de-portas-em-Python
Ele serve para verificar quais portas de um dispositivo estão abertas na rede.
import socket

target = input("Digite o IP alvo: ")

ports = [21, 22, 80, 443, 3306]

for port in ports:
    client = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
    client.settimeout(1)

    result = client.connect_ex((target, port))

    if result == 0:
        print(f"Porta {port} aberta")
    else:
        print(f"Porta {port} fechada")

    client.close()