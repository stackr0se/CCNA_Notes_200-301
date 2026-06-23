# Intro to CLI

What is a CLI
- A command-line interface
- The interface you use to configure Cisco devices

# How do you connect to a Cisco device? (Console port)
- You can connect to either the USB Mini-b or the RJ45

To connect to a RJ45 do you need this
- Most laptops no longer have a serial port to plug the cable into so you need an adapter
<img width="1005" height="495" alt="image" src="https://github.com/user-attachments/assets/66f51d59-7ef7-4c32-90a0-300c5c2fdfcf" />

# How do you actually access the CLI?

You need to use a Terminal Emulator, PuTTy is a popular choice. After you click serial then open to connect to the CLI

When you first enter the CLI, you will by default be in 'User EXEC Mode'
Hostname>
 > = user EXEC Mode
- User EXEC mode is very limited.
- Users cna look at some things, but can't make any changes to the configuration.
- Also called 'user mode'

If you enter 'enable' it will place you into Privileged EXEC Mode

Privileged EXEC Mode
- Provides complete access to view the device's configuration, restart the device, etc.
- Cannot change the configuration, but can change th etime on the device, save the configuration file, etc.

- "Router>enable"
- "Router#" # = privileged EXEC mode

You can use a question mark to see the commands avaible to you
<img width="1005" height="495" alt="image" src="https://github.com/user-attachments/assets/1168e315-d0b5-4cf2-ba60-255efd462665" />

# Global Configuration Mode
- To make changes to the router configuration you need to enter global configuraiton mode
- The command is "configure terminal" or "conf t"
- When in global configuration mode, config is inserted after the hostname

# To Enable Password for User in EXEC mode
- use the 'enable command to enter privileged exec mode
- from privileged exec mode, I enter configure terminal to enter global configuration
- In global configuration you enter "enable passworld [ name of password]" (case sensetive)

There are two different seperate configuration files kept on the device at once
- Running-config = the current, active configuration file on the device. As you enter commands in the CLI, you edit the active configuration.
- Startup-config = the configuration file that wil be loaded upon restart of the device
- you can use the command 'show running-config' to view the running config
- you can use the command 'show startup-config' to view startup-config

To save the configuration (exec mode)
- 'write'
- 'write memory'
- 'copy running-config startup-config'

To encrypt passwords
- enter global configuration mode "conf t"
- then the command "service password-encryption"
- the more secure method is to use the "enable secret" command

To cancel/delete a command you entered, use the command "no" infront of the command

If you enable service password-encruption
- current passwords will be encrypted
- future passwords will be encrypted
- the enable secret will not be effected

if you disable service password-encryption
- current passwords will not be decrypted
- future passwords will not be encrypted
- the enable secret will not be effected
<img width="2000" height="1120" alt="image" src="https://github.com/user-attachments/assets/7bf7e4a8-56f3-4308-8e03-194adfe19268" />
<img width="2000" height="1110" alt="image" src="https://github.com/user-attachments/assets/2c94a490-3f51-4576-8522-59142f223860" />
<img width="2000" height="1114" alt="image" src="https://github.com/user-attachments/assets/f65dd309-18d4-441c-bc71-34a7aec43b4a" />
<img width="2000" height="1117" alt="image" src="https://github.com/user-attachments/assets/804d7cb3-7c83-491d-a2de-2c4a04802aad" />
<img width="2000" height="1115" alt="image" src="https://github.com/user-attachments/assets/7f702ae4-bbeb-4a7a-9d7a-180057cc4a40" />
