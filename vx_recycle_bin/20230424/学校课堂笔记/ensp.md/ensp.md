# ensp
1. vlan batch  创建vlan
2. [SW1]stp mode rstp

[SW2]stp mode rstp

[SW3]stp mode rstp

[SW4]stp mode rstp

    设置汇聚层交换机SW1为根交换机，SW2为备份根交换机。

[SW1]stp root primary

[SW2]stp root secondary


3. 链路聚合
SW1]interface Eth-Trunk ?
\<0-63> Eth-Trunk interface number
[SW1]interface Eth-Trunk 1 #创建逻辑的捆绑接口组1
[SW1-Eth-Trunk1]quit
// 或 trunkport g 0/0/1 to 0/0/2 加入接口
[SW1]interface gi0/0/1
[SW1-GigabitEthernet0/0/1]eth-trunk 1 #将接口加入端口组1
[SW1-GigabitEthernet0/0/1]interface gi0/0/2
[SW1-GigabitEthernet0/0/2]eth-trunk 1
[SW1-GigabitEthernet0/0/2]interface gi0/0/3
[SW1-GigabitEthernet0/0/3]eth-trunk 1

4. 配置vlan
[LSW1-Eth-Trunk12]port link-type trunk    //将链路设置trunk模式
[LSW1-Eth-Trunk12]port trunk allow-pass vlan 1 10 20 30
[LSW1]display eth-trunk      //查看eth-trunk的状态
[LSW1-GigabitEthernet0/0/3]port link-type access 
[LSW1-GigabitEthernet0/0/3]port default vlan 40
[LSW1]port-group 1
[LSW1-port-group-1]group-member g0/0/4 to g0/0/5
[LSW1-port-group-1]port link-type trunk 
[LSW1-port-group-1]port trunk allow-pass vlan 10 20 30

LSW3/4   Eth 接口！！！

5. 配置VRRP协议
[LSW1-Vlanif10]vrrp vrid 10 virtual-ip 10.1.1.1 
[LSW1-Vlanif10]vrrp vrid 10 priority 120

6. ospf
[AR1]ospf 100 router-id 1.1.1.1
[AR1-ospf-100]area 0
[AR1-ospf-100-area-0.0.0.0]net 10.1.4.1 0.0.0.0
[AR1-ospf-100]default-route-advertise 下发路由

7. DHCP
[LSW1]dhcp enable 
[LSW1-Vlanif30]dhcp select interface 
[LSW1-Vlanif30]dhcp server dns-list 8.8.8.8
static-bind ip-address 10.1.3.10 mac-address 54-89-98-30-6F-15 //给指定PC分配固定IP地址
dhcp server excluded-ip-address 192.168.1.1 192.168.1.100  使该范围ip不参与分配

[LSW1-Vlanif30] dhcp server excluded-ip-address 10.1.3.11 10.1.3.99
[LSW1-Vlanif30]  server excluded-ip-address 10.1.3.101 10.1.3.254


8. NAT
[AR1]nat address-group 1 202.100.1.10 202.100.1.10
[AR1]ip route-static  0.0.0.0 0.0.0.0 202.100.1.2
[AR1-Serial1/0/0]nat outbound 3000 address-group 1 

acl 3000
[AR1-acl-adv-3000]rule deny icmp source 10.1.1.0 0.0.0.255 destination 11.1.1.0  0.0.0.255   配置拒绝访问目标

[AR1-acl-adv-3000]rule permit ip source any destination any 

[AR1-acl-adv-3000]rule permit tcp source 10.1.1.0 0.0.0.255 destination 11.1.1.1
00 0
traffic-filter inbound acl 3000

