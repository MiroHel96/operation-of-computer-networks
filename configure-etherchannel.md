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


# Part 2 Configure an EtherChannel with Cisco PAgP

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



# Part 3 Configure an 802.3ad LACP EtherChannel


# Part 4 Configure a Redundant EtherChannel Link

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
