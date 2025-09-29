# Cisco Packet Tracer - Configure EtherChannel

In this excersise I configure different types of EtherChannels 



## Topology of the network

<img width="727" height="353" alt="image" src="https://github.com/user-attachments/assets/00297273-fb4b-4964-b89c-7f8303ccb07b" />


## Port Channel Table 

<img width="697" height="209" alt="image" src="https://github.com/user-attachments/assets/7d82b990-2b7e-43e1-be65-63e8bf48dbe8" />


# Part 1 Configure Basic Switch settings

First step was to assign hostname for each device: 
`S1`, `S2` and `S3`

I opened each switches terminal and entered privileged EXCEC -mode to set hostname for each switch. 

<img width="655" height="483" alt="image" src="https://github.com/user-attachments/assets/e0160581-63ae-4282-bc17-253802df90cb" />

After setting name for each device I saved the configuration in privileged mode with `copy running-config startup-config`.

Before beginning `link aggregation` which is combining several physical links to one logical link. In Cisco environment it is `EtherChannel`. I must verify settings for each interface according EtherChannel guidelines in the end of this document. 

Example of `S1`

Command `S1# show interfaces | include Ethernet` includes word Ethernet with piping.

<img width="642" height="425" alt="image" src="https://github.com/user-attachments/assets/b865e4d4-a99c-4ccc-a8cb-fb7575b88327" />

Command `S1# show interface status` shows interfaces name, status, Vlan, Duplex, Speed and type. In this case Vlan 1, Duplex auto and speed auto.

<img width="674" height="569" alt="image" src="https://github.com/user-attachments/assets/67ca0013-4b60-461b-bb65-55b9904f5039" />

Command `S1# show interfaces trunk`, shows if there are trunk ports configured in the switch. S1 does not have any.

<img width="659" height="119" alt="image" src="https://github.com/user-attachments/assets/3fffa9a0-c1d4-4145-b8eb-75a288b3c481" />

There is no trunk ports configured in any of the switches therefore I must configure every connected interface as a trunk port. 

I opened S1 terminal and used the following commands:

- `configure terminal`
- `interface range fastEthernet 0/21-22`
- `switchport mode trunk`
- `switchport trunk native vlan 1`

Next I configured GigabitEthernet with the same settings.

<img width="642" height="270" alt="image" src="https://github.com/user-attachments/assets/84029d4c-40ee-4030-9f3f-81e287b7606e" />

<img width="638" height="254" alt="image" src="https://github.com/user-attachments/assets/a270f286-2d52-4ed0-a108-ebe2cba4f06e" />

<img width="636" height="85" alt="image" src="https://github.com/user-attachments/assets/c4620447-56ff-4b29-be77-373cf5b3687e" />

After configuration I verified correct settings with command `show interfaces trunk`

<img width="636" height="350" alt="image" src="https://github.com/user-attachments/assets/eb0c9869-3c1c-47f7-937b-e114054098c3" />

After S1 I configured settings for S2 and S3 according to the Port Channel Table. 

Finally I used command `switchport nonegotiate` to suppress DTP frames and reduce unnecessary traffic.


# Part 2 Configure an EtherChannel with Cisco PAgP (Port Aggregation Protocol).

Before configuring PAgP to ports I manually shut them down. It is recommended when cofigurin EtherChannels, because EtherChannel Misconfig Guard may place these ports into err-disabled state.

I issued each interface with the following command `shutdown`

Example of S3

<img width="638" height="186" alt="image" src="https://github.com/user-attachments/assets/0aefe5f9-cbae-4e13-a212-967be104b577" />

I opened S1 CLI and entered following commands:
- `interface range f0/21-22`
- `channel-group 1 mode desirable`, this sets the port to channel 1 and the mode desirable enables the switch to actively negotiate to form a PAgP link. 
- `no shutdown`

<img width="789" height="624" alt="image" src="https://github.com/user-attachments/assets/e5f7812a-36ed-4d06-8ca7-d57c80917251" />

After S1 I did the same for S3. 

Next I configured the logical interface to become a trunk port. In this case it's `Channel 1`. 

I used the following commands in S1 and S3:
- `interface port-channel 1`
- `switchport mode trunk`

<img width="635" height="211" alt="image" src="https://github.com/user-attachments/assets/3a072ab3-c21f-4aef-b248-934340ce4cec" />

End result. The links are green so it is working as expected.

<img width="658" height="330" alt="image" src="https://github.com/user-attachments/assets/cfcb4e3a-ab1d-4809-8297-4cfbcc4e24d9" />

I confirmed this from S1 using command `show etherchannel summary`, as we can see from the result. Port-channel has flags S = Layer2 and U = in use. Now I have configured EtherChannel between S1 and S3.

<img width="640" height="285" alt="image" src="https://github.com/user-attachments/assets/15921ef4-f51c-400e-bb7c-9ae3fc87e154" />


# Part 3 Configure an 802.3ad LACP EtherChannel

Next I configure `IEEE released 802.3ad, which is an open standard version of EtherChannel. It is commonly referred to as LACP.`. It works with different vendor's devices and it is not Cisco proprietary.

I configured S1 with the following commands:
- `interface range g0/1 - 2`
- `channel-group 2 mode active`
- `no shutdown`
  
- `interface port-channel 2`
- `switchport mode trunk`

<img width="662" height="677" alt="image" src="https://github.com/user-attachments/assets/8726c367-ecd4-4959-826e-fcd96fceede1" />

<img width="658" height="495" alt="image" src="https://github.com/user-attachments/assets/92137620-9f19-4ff6-a581-252bd4647a00" />

No I have configured LACP (Link Aggregation Control Protocol) to S1 G0/1-2 ports, but it's still in down state. I have to configure S2 next with the same settings.

<img width="631" height="284" alt="image" src="https://github.com/user-attachments/assets/5094444e-d959-42d9-9949-7115f1905061" />

<img width="635" height="314" alt="image" src="https://github.com/user-attachments/assets/3398fe9c-7933-4776-a5ce-013388096c1c" />


# Part 4 Configure a Redundant EtherChannel Link

Next I had to configure Port Channel 3 for switch S2. 

I used the following commands for S2: 
- `interface range f0/23 - 24`
- `channel-group 3 mode passive`, LACP is only used if another LACP device is detected. 
- `no shutdown`

- `interface port-channel 3`
- `switchport mode trunk`


<img width="639" height="598" alt="image" src="https://github.com/user-attachments/assets/46ad6da5-2f1c-4061-b4c0-8048ce1ceb8f" />

Next I configured F0/23-24 interfaces in S3 with the same commands as S2. Except I set channel-group 3 mode to `active`. So S3 interfaces will actively try to seek another LACP port.

<img width="639" height="923" alt="image" src="https://github.com/user-attachments/assets/fc77606b-98bd-4b48-a45a-15281d8d4176" />

No everything Is set, but STP is still blocking GigaBit ports. I have to restore these settings by configuring S1 to be primary root for VLAN 1.

<img width="615" height="330" alt="image" src="https://github.com/user-attachments/assets/a05c00a2-b74a-4318-9766-3eb60ca28f8a" />

I used the following command: `spanning-tree vlan 1 root primary`, alternatively I could also had set priority to `24576` with command: `spanning-tree vlan 1 priority 24576`.

<img width="615" height="147" alt="image" src="https://github.com/user-attachments/assets/290eb2ce-6293-4680-82b7-a2bea08e8e3f" />

Now I have successfully configured different EtherChannels for Cisco network. 

<img width="620" height="340" alt="image" src="https://github.com/user-attachments/assets/7648e49c-97cd-4852-be55-9f452968f7ef" />


# EtherChannel Configuration Guidelines and Restrictions

```EtherChannel has some specific guidelines that must be followed in order to avoid configuration problems.

1)    All Ethernet interfaces support EtherChannel up to a maximum of eight interfaces with no requirement that the interfaces be on the same interface module.

2)    All interfaces within an EtherChannel must operate at the same speed and duplex.

3)    EtherChannel links can function as either single VLAN access ports or as trunk links between switches.

4)    All interfaces in a Layer 2 EtherChannel must be members of the same VLAN or be configured as trunks.

5)    If configured as trunk links, Layer 2 EtherChannel must have the same native VLAN and have the same VLANs allowed on both switches connected to the trunk.

6)    When configuring EtherChannel links, all interfaces should be shutdown prior to beginning the EtherChannel configuration. When configuration is complete, the links can be re-enabled.

7)    After configuring the EtherChannel, verify that all interfaces are in the up/up state.

8)    It is possible to configure an EtherChannel as static, or for it to use either PAgP or LACP to negotiate the EtherChannel connection. The determination of how an EtherChannel is setup is the value of the channel-group number mode command. Valid values are:

active LACP is enabled unconditionally

passive LACP is enabled only if another LACP-capable device is connected.

desirable PAgP is enabled unconditionally

auto PAgP is enabled only if another PAgP-capable device is connected.

on EtherChannel is enabled, but without either LACP or PAgP.

9)    LAN ports can form an EtherChannel using PAgP if the modes are compatible. Compatible PAgP modes are:

desirable => desirable

desirable => auto

If both interfaces are in auto mode, an Etherchannel cannot form.

10)  LAN ports can form an EtherChannel using LACP if the modes are compatible. Compatible LACP modes are:

active => active

active => passive

If both interfaces are in passive mode, an EtherChannel cannot form using LACP.

11)  Channel-group numbers are local to the individual switch. Although this activity uses the same Channel-group number on either end of the EtherChannel connection, it is not a requirement. Channel-group 1 (interface po1) on one switch can form an EtherChannel with Channel-group 5 (interface po5) on another switch.

Cisco - Packet Tracer

```
