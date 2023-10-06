# Wireshark Challenge - Carnage

## Desciption
Wireshark is an open-source, cross-platform network packet analyser tool capable of sniffing and investigating live traffic and inspecting packet captures (PCAP). It is commonly used as one of the best packet analysis tools. In this lab, I will run through a scenario using Wireshark to analyze network traffic and detect suspicious activities.

## Table of Contents

   * [Languages and Utilities Used](#Languages-and-Utilities-Used)
   * [Environments Used](#Environments-Used)
   * [Walk-Through](#Walk-Through)

## Languages and Utilities Used

* **Wireshark** 

## Environments Used

* **Ubuntu 18.04.6 LTS**

## Walk-Through

### Scenario

Eric Fischer from the Purchasing Department at Bartell Ltd has received an email from a known contact with a Word document attachment. Upon opening the document, he accidentally clicked on "Enable Content."  The SOC Department immediately received an alert from the endpoint agent that Eric's workstation was making suspicious connections outbound. The pcap was retrieved from the network sensor and handed to you for analysis. 

**Task:** Investigate the packet capture and uncover the malicious activities. 

### Q1) What was the date and time for the first HTTP connection to the malicious IP?

First we need to view only the HTTP traffic using the following filter: `http`

The defualt time format is in seconds since beginning of capture. Since we are looking for the date and time of the first HTTP connection, we need to change the time format to UTC.

<img src="https://github.com/emann615/emann615/assets/117882385/1b563f4f-3b7c-4d79-9a1c-e85b4e02bfe5" height="70%" width="70%"/>
</br>
</br>

Now we can see the date and time of the first HTTP connection to the malicious IP.

<img src="https://github.com/emann615/emann615/assets/117882385/308a0aa5-700c-458c-9074-b4c56222fc50" height="100%" width="100%"/>
</br>
</br>

**A1) 2021-09-24 16:44:38**

### Q2) What is the name of the zip file that was downloaded?

If look back at that first HTTP connection, we can see that it is a GET request for a zip file.

<img src="https://github.com/emann615/emann615/assets/117882385/0685cd64-f5b4-41a7-9279-27e8c42a5c62" height="50%" width="50%"/>
</br>
</br>

**A2) documents.zip**

### Q3) What was the domain hosting the malicious zip file?

To find the domain, we need to view the HTTP headers for the GET request. We can find the HTTP headers by looking in the Packet Details Pane. The domain is next to the Host header.

<img src="https://github.com/emann615/emann615/assets/117882385/cfcb9d16-ce6c-444b-86b7-6d1b53f6d2c7" height="50%" width="50%"/>
</br>
</br>

**A3) attirenepal.com**


<img src="" height="70%" width="70%"/>
</br>
</br>
