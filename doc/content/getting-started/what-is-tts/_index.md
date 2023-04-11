---
title: "What Are LoRaWAN and The Things Stack?"
description: ""
weight: -2
---

Welcome to {{% tts %}}! In this section, we help you to understand how to use {{% tts %}}, who makes it, and common acronyms like TTS, TTI, and TTN.

If you are already familiar with LoRaWAN, you can skip ahead and [setup your own LoRaWAN network]({{< relref "setup-first-network" >}}).

<!--more-->

## What is LoRaWAN?

Here is a video of Johan Stokking, the tech lead of The Things Industries and one of the core developers of {{% tts %}}, explaining LoRaWAN:

{{< youtube "ZsVhYiX4_6o" >}}

{{< note >}} Some common [use cases](https://www.thethingsnetwork.org/docs/lorawan/what-is-lorawan/#lorawan-use-cases) are explained in the video above, but there are certain limitations that make LoRaWAN not suitable for every use-case. Read about [LoRaWAN limitations in The Things Network LoRaWAN documentation](https://www.thethingsnetwork.org/docs/lorawan/limitations/). {{</ note >}}

## LoRaWAN

LoRa is a wireless modulation technique that encodes information on radio waves using chirp pulses - similar to the way dolphins and bats communicate! LoRa modulated transmission is robust against disturbances and can be received across great distances.

LoRaWAN is a Media Access Control (MAC) layer protocol built on top of LoRa modulation. It is a software layer which defines how devices use the LoRa hardware, for example when they transmit, and the format of messages.

The LoRaWAN protocol is developed and maintained by the LoRa Alliance. The first LoRaWAN specification was released in January 2015. The table below shows the version history of the LoRaWAN specifications. At the time of this writing the latest specifications are 1.0.4 (in 1.0 series) and 1.1 (1.1 series).

### Architecture

Sensor networks in LoRaWAN are deployed in a star-of-stars topology.

{{< figure src="architecture.png" alt="LoRaWAN architecture" >}}

A typical LoRaWAN network consists of the following basic parts.

**End Devices**
  - Sensors or actuators send LoRa modulated wireless messages to the gateways or receive messages wirelessly back from the gateways. .

**Gateways**
  - Specialized evices that receive messages from end devices and forward them to the Network Server.

**Network Server**
  - A piece of software running on a server that manages the end devices.
  - Also referred to as LoRaWAN Network Server/LNS or simply Network software.

**Application servers**
  -  A piece of software running on a server that is responsible for securely processing application data.

### Message Flow

End devices communicate with nearby gateways and each gateway is connected to the network server. Messages sent from end devices travel through all gateways within range.

These messages are received by the Network Server. If the Network Server has received multiple copies of the same message, it keeps a single copy of the message and discards others. This is known as message deduplication.

The messages that originates from an end device are called an Uplinks.

Messages flowing in the opposite direction (originating from the Network Server and/or Application Server and sent to end devices) are called Downlinks.

### Security

All LoRaWAN data is encrypted AES-128 symmetric keys.

Application data is encrypted using a particular key. This key is only shared between the Application Server and the End Device.

Network (settings) data is encrypted using a different key. This key is only shared between the Network Server and the End Device.

All devices have a key called the "Root Key" associated with them. The separate keys for the application data and network data are derived from this root key.

{{< note "These keys are called Session Keys since they are rotated when a device session changes. Device sessions are a much deeper topic and is omitted from this basic guide in the interest of simplicity. See the linked references for more information." />}}

## What is {{% tts %}}?

{{% tts %}} an enterprise-grade LoRaWAN Network Server that contains services and tools to securely install and manage millions of LoRaWAN devices in production. In addition, {{% tts %}} contains services and tools to securely manage millions of LoRaWAN devices in production.

### {{% tts %}} Deployments

#### Professional

{{% tts %}} offers the following options for LoRaWAN deployments in production. For pricing and information about all available deployments, see [The Things Industries Deployments Page](https://www.thethingsindustries.com/deployment/).

{{< distributions "Cloud" >}} **Cloud**: The quickest way to get started with LoRaWAN is to sign up to [{{% tts %}} Cloud]({{< ref "the-things-stack/host/cloud" >}}) a fully-managed SLA-backed cloud subscription. By using {{% tts %}} Cloud, you can focus on scaling your LoRaWAN deployments while leaving the complexity of managing a production LoRaWAN Network Server to us. The Things Stack Cloud offers a [free discovery tier](https://www.thethingsindustries.com/stack/plans/) to get started and is the recommended option for most new users.

{{< distributions "Dedicated Cloud" >}} **Dedicated Cloud**: All the benefits of **Cloud** on a dedicated cluster.

{{< distributions "AWS Launcher" >}} **AWS Launcher**: AWS marketplace makes it easy to deploy in one click on new or existing EC2 cluster. Integrates effortlessly with AWS IOT, so you can keep using tools you're already familiar with. See [AWS]({{< ref "the-things-stack/host/aws" >}}).

{{< distributions "Enterprise" >}} **Enterprise**: Install the network server on your own hardware, with professional support from The Things Industries. If you prefer to take on the responsibility of installing and maintaining {{% tts %}} in addition to managing your LoRaWAN device fleet,  {{% tts %}} is available to be [installed on your own hardware or cloud infrastructure]({{< ref "the-things-stack/host/docker" >}}).

#### Community 

For simple community projects and local testing, there are a few options.

{{< distributions "Community" >}} **Community Edition**: A free and limited version of {{% tts %}} is available to [The Things Network](https://www.thethingsnetwork.org/) community for simple proof-of-concepts and community projects. This service comes with no uptime guarantees.

{{< distributions "Open Source" >}} **Open Source**: For DIY'ers, the core of {{% tts %}} is [open source](https://github.com/thethingsnetwork/lorawan-stack) and available for local testing.

## Who makes {{% tts %}}?

{{% tts %}} is developed and maintained by [The Things Industries](https://thethingsindustries.com/).

The Things Industries offers several types of deployments of {{% tts %}}, for example as a managed cloud service, or with additional proprietary features.

## What are TTI, TTN, and TTS?

You might see abbreviations like TTN, TTS, and TTI tossed around in the forums and in other places. Here's what they mean:

### TTS: {{% tts %}}

TTS is {{% tts %}}, the LoRaWAN Network Server stack. {{% tts %}} is currently at version 3 of a Network Server implementation, and is therefore also informally known as V3.

### TTN: The Things Network

TTN is [The Things Network](https://thethingsnetwork.org), which is a global collaborative Internet of Things ecosystem that creates networks, devices and solutions using LoRaWAN. The Things Network runs {{% tts %}} Community Edition, which is a crowdsourced, open and decentralized LoRaWAN network. This network is a great way to get started testing devices, applications, and integrations, and get familiar with LoRaWAN.

### TTI: The Things Industries

TTI is The Things Industries: the company primarily responsible for development of {{% tts %}} and writing documentation. The Things Industries also offers cloud hosted and on-premises private LoRaWAN networks with additional enterprise features, and premium support plans for enterprise clients. If you're interested in building your own guaranteed uptime enterprise grade LoRaWAN network, send us an [email](mailto:info@thethingsindustries.com).
