---
layout: post
title: "How to Set AD and ADFS"
description: ""
category: setup
tags: ['windows']
---
{% include JB/setup %}

# How to set AD and ADFS in AWS

## Preparation
1. Download a RDP software, If you use Mac, I prefer Remote Desktop Connection because Cord may come with some lost connection issue.
2. Download [Active Directory Federation Services 2.0 RTW](http://www.microsoft.com/en-us/download/details.aspx?id=10909)

### Step1: Apply for AWS account
nothing special

### Step2: Get a Windows Server Free Tier
1. get the win2008R2 with basic AD..
2. In security group settings, allow RDP/http/https/LDAP

### Step3: Create a Domain Controller
1. when come with DNS options, choose yes
2. domain name is like **department.company.com**

### Step4: Add IIS role and Create a Certificate
1. When asked to input some name, use the Computer name, like WIN-XXXXXXXX
2. You need to to create a self-signed Certificate by clicking "Create Self-Signed Certificate" link

### Step5: Download and Install ADFS
1. Go on with the default values, for attribute Store: Active Directory
LDAP Attribute email address = outgoing claim type Name ID
LDAP attribute Given-Name = Outgoing claim type Given Name.
2. Launch ADFS2.0 Management Utility, Click the "Token-signing"=>View Certificate=>Copy to file=> Next=>Choose Base-64 encoded X.509(.CER)

### Step6: Add Relying Trust
1. Import the sp.xml from the service provider
2. right click the relying trust, change secure hash algorithm to SHA-1

## Reference:


**Internet Resources**

[Domain Controller Install](http://www.rackspace.com/knowledge_center/article/installing-active-directory-on-windows-server-2008-r2-enterprise-64-bit)

[ADFS Setup](https://cd.centraldesktop.com/adn/doc/13243242/)