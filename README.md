# Setting up a Kenet-InfluxDB Instance for IoT Timeseries Data

## Introduction

InfluxDB is an open-source database for storing time series data. This data can come from logging and monitoring systems or from IOT (Internet of Things) devices. KENET, Kenya Education Network, is Kenya's National Research and Education Network. It serves education and research institutions in Kenya by providing internet connectivity, cloud services(processing and storage) and research grants. Highlighted in this repository is a procedure on how to setup an InfluxDB database on a kenet server that in turn stores data from IoT sensor nodes. Figure.1 is a block diagram that highlights the entire system. 

| ![kenet1](/img/block2.PNG) | 
|:--:| 
| *Figure 1: River Water level Data Aquisition Block Diagram showing the Integration of a Kenet - Influx Virtual Machine* |

## Pre-Requisites / Requirements

- Kenet Vlab access to create a virtual machine (Linux machine) = The access is provided by Kenet after verifying your Vlab access request. Also, a verified user can create a machine that can be accessed by a non-verified user via  **[Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)**.
- Putty = On your personal computer to access the virtual machine command line (SSH).

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

| ![putty3](/img/putty33.jpg) | 
|:--:| 
| *Figure 3: After clicking open* |

| ![putty4](/img/putty44.jpg) | 
|:--:| 
| *Figure 4: After keying in the password and running **sudo su** to enable root* |

## Installing InfluxDB on the Linux machine

To install influxdb, run the following commands sequentially 

1. `curl -sL https://repos.influxdata.com/influxdb.key | sudo apt-key add -`

2. `echo "deb https://repos.influxdata.com/ubuntu trusty stable" | sudo tee /etc/apt/sources.list.d/influxdb.list`

| ![putty5](/img/putty55.jpg) | 
|:--:| 
| *Figure 5: Step 1 and 2 output* |

3. `apt update`

4. `apt install influxdb influxdb-client python3-influxdb`

5. `systemctl enable influxdb`

6. `systemctl start influxdb`

In order to check if the installation went well, you can use the client to execute a basic Influxdb query as shown on Figure 6.



