# Setting up a Kenet-InfluxDB Instance for IoT Timeseries Data

## Introduction
InfluxDB is an open-source database for storing time series data. This data can come from logging and monitoring systems or from IOT (Internet of Things) devices. KENET, Kenya Education Network, is Kenya's National Research and Education Network. It serves education and research institutions in Kenya by providing internet connectivity, cloud services(processing and storage) and research grants. Highlighted in this repository is a procedure on how to setup an InfluxDB database on a kenet server that in turn stores data from IoT sensor nodes. Figure.1 is a block diagram that highlights the entire system. 

![kenet1](/img/block2.PNG)

## Pre-Requisites / Requirements
- Kenet Vlab access to create a virtual machine (Linux machine) = The access is provided by Kenet after verifying your Vlab access request. Also, a verified user can create a machine that can be accessed by a non-verified user via  **[Putty](https://www.chiark.greenend.org.uk/~sgtatham/putty/latest.html)**.
- Putty = On your personal computer to access the virtual machine command line (SSH).
