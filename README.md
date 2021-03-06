# ESET Tools by Robbie Ferguson

These tools are scripts I've written to help me or my customers. They're not necessarily "officially endorsed" by ESET, though ESET may at times use them to support customers. Feel free to use them in your environment. Always have a good backup, because most of these scripts do something that could be destructive. They're here to make usually complicated tasks simple. Hope you enjoy!

## Tool # 1: Install MDC on ERA OVA (v6) or ESMC OVA (v7)

Activate your ERA or ESMC server as a standard management server, and then SSH to the appliance and run the following command to add ESET Mobile Device Connector to it. This removes the need to have a separate ESET Mobile Connector virtual appliance running on your hypervisor and puts both components on the same virtual server.

### For ESET Security Management Center (ESMC v7)
```
yes | yum install git && mkdir -p /root/eset_installers/thirdparty/ && cd /root/eset_installers/thirdparty/ && git clone https://github.com/Cat5TV/eset && /root/eset_installers/thirdparty/eset/esmcmdc prep
```

### For ESET Remote Administrator (ERA v6)
```
yes | yum install git && mkdir -p /root/eset_installers/thirdparty/ && cd /root/eset_installers/thirdparty/ && git clone https://github.com/Cat5TV/eset && /root/eset_installers/thirdparty/eset/eramdc prep
```

Following installation, you must:

1. Create a ESET Mobile Device Connector certificate. Use your appliance's LAN IP address as the hostname.
2. Create a ESET Mobile Device policy. Add the certificate, and assign it to your ERA/ESMC appliance.

## Tool # 2: Uninstall ESET Management Agent / ESET Remote Administrator Agent

Should you need to uninstall your ESET agent without a Client Task (as would be the case if your ERA/ESMC server was no longer available), you can use [uninstallers/eset-uninstall-agent.bat](uninstallers/eset-uninstall-agent.bat) as a GPO, or manually run as administrator.
