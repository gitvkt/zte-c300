# comandoszte
COMANDOS OLT ZTE


******************************************************************************************
# Verificar ONUs não cadastradas

zte#show pon onu uncfg
******************************************************************************************
# Ver todas ONUS em um PON e porta

zte#show gpon onu baseinfo gpon-olt_1/8/2

Exemplo para verificar no Slot 1 da Porta 8 na Pon 2
******************************************************************************************
# Cadastrar uma ONT

zte(config)#interface gpon-olt_1/8/2

zte(config-if)#onu 50 type F660 sn AABCEF123456 

.[Successful]

zte(config-if)#!

zte(config)#interface gpon-onu_1/8/2:50

zte(config-if)#name NOKIA2-TESTE-9-8/2:50

zte(config-if)#sn-bind enable sn

zte(config-if)#tcont 1  profile 1G

zte(config-if)#gemport 1  tcont 1

zte(config-if)#service-port 1 vport 1 user-vlan 101  vlan 101 

zte(config-if)#!

zte(config)#pon-onu-mng gpon-onu_1/8/2:50

zte(gpon-onu-mng 1/8/2:50)#service 1 gemport 1 vlan 101

zte(gpon-onu-mng 1/8/2:50)#!

zte(config)#exit

zte#wr


Exemplo de VLAN: 101

Exemplo de nome:  NOKIA2-TESTE-9-8/2:50

Exemplo de número de série:  AABCEF123456

Exemplo de profile: 1G

Exemplo para cadastrar no Slot 1 da Porta 8 da Pon 2 na Posição 50

******************************************************************************************

# Remover um ONU

conf t

interface gpon-olt_1/8/2

no onu 50

.[Successful]

exit

exit

wr
******************************************************************************************
