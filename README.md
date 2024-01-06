# SDN-Perform-Topology-Linear
Performance Analysis of ONOS and ODL Controllers on linear topology

Topology Linear 6 Node ( 6 Sw & 6 Host)
### Version
- Ubuntu 18.04
- Onos: 2.0.0
- Opendayligth: 0xygen (0.8.4)

## Performance Parameter Quality Of Service (QOS)
- Bandwith
- Throughput
- Latency/Delay
- Jitter
- Packet Loss

## Mininet Instalitation
- Install Git
  `sudo apt-get install git`
- Clone mininet
  `git clone https://github.com/mininet/mininet`
- Pyhton Mininet
  `sudo PYTHON=python2 mininet/util/install.sh -n`
- Installation mininet
  `mininet/util/install.sh -a`
## Controller
  ### ONOS
  - Add user sdn
  `sudo adduser sdn --system --group`
  - Install java 8
  `sudo apt install git zip curl unzip python-minimal openjdk-8-jdk -y`
  - Make folder opt (if u dont make before)
    `sudo mkdir -p /opt && cd /opt`
  - Go to dir Onos and wget onos
    `sudo wget https://repo1.maven.org/maven2/org/onosproject/onos-releases/2.0.0/onos-2.0.0.tar.gz`
  - Extract tar file onos
    `sudo tar xzf onos-2.0.0.tar.gz`
  - Move the extraction results to onos to /opt
    `sudo mv onos-2.0.0 /opt/onos`
  - Then, go to dir opt
  - Change ownership
    `sudo -u sdn nano /opt/onos/options`
  - Input config
    `# running onos with user sdn
export ONOS_USER=sdn`
`# default active drivers and openflow
export ONOS_APPS=drivers,openflow,gui2`
  - Install Service Onos
    `sudo cp /opt/onos/init/onos.initd /etc/init.d/onos
sudo cp /opt/onos/init/onos.service /etc/systemd/system/
sudo systemctl daemon-reload
sudo systemctl enable onos`
  - Start Onos
    `sudo systemctl start onos`
  - Status Onos
    `sudo systemctl status onos`
  - Stop Onos
    `sudo systemctl stop onos`
 ## OpenDaylight
 - Install java JDK8
   `sudo apt-get -y install openjdk-8-jre`
   `sudo update-alternatives --config java`
   `sudo echo 'export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre' >> ~/.bashrc`
   `source ~/.bashrc`
 - Make folder karaf
   `sudo mkdir /usr/local/karaf`
 - Go to dir download for download odl and extract
   `cd download/`
   `sudo wget https://nexus.opendaylight.org/content/repositories/opendaylight.release/org/opendaylight/integration/karaf/0.8.4/`
   `sudo tar -zxf karaf-0.8.4.tar.gz`
 - Move file extract to karaf folder
   `sudo mv ~/Downloads/karaf-0.8.4 /usr/local/karaf/`
 - Install karaf
   `sudo update-alternatives --install /usr/bin/karaf karaf /usr/local/karaf/karaf-0.8.4/bin/karaf 1`
   `sudo update-alternatives --config karaf`
 - Run ODL
   `sudo -E karaf`
# Quality of Service
 ## Bandwidth:
- Server (h1): iperf -s
- Client (h2): iperf -c <IP_server> -t <duration> -b <bandwidth>
- Replace <IP_server> with IP address h1.
- Replace <duration> with the measurement duration (for example, 10 seconds).
- Replace <bandwidth> with the desired bandwidth (for example, 1M for 1 Mbps).

 ## Throughput:
- Server (h1): iperf -s
- Client (h3): iperf -c <IP_server> -t <duration>
- Replace <IP_server> with IP address h1.
- Replace <duration> with the measurement duration (for example, 10 seconds).

## Packet Loss:
- Server (h1): iperf -s
- Client (h4): iperf -c <IP_server> -t <duration> -l <packet_size>
- Replace <IP_server> with IP address h1.
- Replace <duration> with the measurement duration (for example, 10 seconds).
- Replace <packet_size> with the desired package size.

## Latency:
- Server (h1): iperf -s
- Client (h5): iperf -c <IP_server> -t <duration> -i <interval>
- Replace <IP_server> with IP address h1.
- Replace <duration> with the measurement duration (for example, 10 seconds).
- Replace <interval> with the measurement interval (for example, 1 second).

## Jitter:
- Server (h1): iperf -s -u
- Client (h6): iperf -c <IP_server> -t <duration> -i <interval> -u -b <bandwidth>
- Replace <IP_server> with IP address h1.
- Replace <duration> with the measurement duration (for example, 10 seconds).
- Replace <interval> with the measurement interval (for example, 1 second).
- Replace <bandwidth> with the desired bandwidth for jitter measurement.
