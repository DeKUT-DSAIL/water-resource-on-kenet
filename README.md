# Setting up a Kenet-InfluxDB Instance for IoT Timeseries Data

## Introduction

InfluxDB is an open-source database for storing time series data. This data can come from logging and monitoring systems or from IOT (Internet of Things) devices. KENET, Kenya Education Network, is Kenya's National Research and Education Network. It serves education and research institutions in Kenya by providing internet connectivity, cloud services(processing and storage) and research grants. Highlighted in this repository is a procedure on how to setup an InfluxDB database on a kenet server that in turn stores data from IoT sensor nodes. Figure.1 is a block diagram that highlights the entire system. 

| ![kenet1](/img/block2.PNG) | 
|:--:| 
| *Figure 1: River Water level Data Aquisition Block Diagram showing the Integration of a Kenet - Influx Virtual Machine* |

## Pre-Requisites / Requirements

- Kenet Vlab access to create a virtual machine (Linux machine) = The access is provided by Kenet after verifying your Vlab access request. Also, a verified user can create a machine that can be accessed by a non-verified user via  **[Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)**.
- Putty = On your personal computer to access the virtual machine command line (SSH).
- preferred Linux Distributtion = Ubuntu 16.04.7 LTS

## Accessing the Kenet Virtual Machine

To access a Kenet virtual machine, a user is provided with 2 access tools to use on Putty.

1. `Hostname (IP address) ending with *vlab.ac.ke*`

2. `A password.`

To access the machine via SSH, a user can utilize putty.

1. `Copy and paste the hostname on the hostname slot on putty (Port = 22 and the connection tyoe should be SSH)`

2. `To avoid filling in the hostname again, a user can save the session by naming it under *Saved Sessions* and clicking on save. After clicking save, the session name appears under *Default Settings*.` 

3. `To load the session, select it and click on *load* and then *open* to access the terminal.` 

Figure 2 shows putty configuration.

| ![putty2](/img/putty2.PNG) | 
|:--:| 
| *Figure 2: Putty Configuration* |

After clicking on *open* the user is prompted to accept the access conditions and the terminal appears. At this point, the user has to paste in the password to enable the command line and also to enable root utilization (sudo su). (NB. To paste on putty = Right click). Figure 3 and Figure 4 shows the process.

| ![putty3](/img/putty3.jpg) | 
|:--:| 
| *Figure 3: After clicking open* |

| ![putty4](/img/putty4.jpg) | 
|:--:| 
| *Figure 4: After keying in the password and running **sudo su** to enable root* |

## Installing InfluxDB on the Linux machine

To install influxdb, run the following commands sequentially 

1. `curl -sL https://repos.influxdata.com/influxdb.key | sudo apt-key add -`

2. `echo "deb https://repos.influxdata.com/ubuntu trusty stable" | sudo tee /etc/apt/sources.list.d/influxdb.list`

| ![putty5](/img/putty5.jpg) | 
|:--:| 
| *Figure 5: Step 1 and 2 output* |

3. `apt update`

4. `apt install influxdb influxdb-client python3-influxdb`

5. `systemctl enable influxdb`

6. `systemctl start influxdb`

In order to check if the installation went well, you can use the InfluxDB client to execute a basic Influxdb query as shown on Figure 6.

7. `influx`

8. `show databases`

| ![putty6](/img/putty6.PNG) | 
|:--:| 
| *Figure 6: Testing the InfluxDB client by running the influx command* |

As shown on Figure 6 the InfluxDB client is up and running. The only database present at this point is the Default: `internal` database.
To exit the Influx shell type `exit`

## Data Transfer from TTN (The Things Network)/(The Things Stack).
To transfer the Water level data from The Things Network to an InfluxDB databases on the Kenet server as shown on Figure 1, we need to run the `ttn-kenet.py` Python Script under assets. The script execution procedure includes.
- Installing Python.
- Creation of an environment with the packages needed to run the script (`requirements.txt` under assets).

### The Things Network
An IoT (Internet of Things) system can be broadly divided into 3 main layers. The first layer is the perception layer which includes sensors and actuators involved in data collection. The second layer is the network layer which is responsible for communication between devices in the system. The network layer includes elements such as gateways and network servers. The last layer is the application layer, where an end user gets to interact with data output.

The network server under the network layer is a crucial component in a deployment scenario. The network server is a central element and is in charge of management of gateways, the authorization of end nodes and the exchange of data (uplink and downlink) between the sensor node and the user application.

The Things Network is a free LoRaWAN network server that is open to all. It has popularized the LoRaWAN technology by offering free services to IoT enthusiasts especially during initial tests before professional deployments.
### Data Rerouting from TNN 

<p  text-align: justify> To transfer data from TTN to another storage service using MQTT, a Data API is utilized. As an MQTT broker, The Things Stack exposes an MQTT to work with streaming events (data from the sensor nodes). Established in 1999, the MQTT is a machine to machine, lightweight, publish/subscribe connectivity protocol for massage queuing service. It is mainly designed for connections with remote locations that have devices with resource constraints such as power or limited network bandwidth such as IoT (Internet of Things). On The Things stack, every application TTS automatically exposes an MQTT endpoint. In order to connect to the MQTT server, an API key that functions as a password is needed. Figure 7 shows the MQTT page on TTN. </p>


| ![putty7](/img/putty7.PNG) | 
|:--:| 
| *Figure 6: Testing the InfluxDB client by running the influx command* |







