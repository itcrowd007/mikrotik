# mikrotik script for two providers
#netwatch 8.8.4.4</br>
</br>
#when UP:
/ip route disable [find comment="ISP-2"]</br>
/ip route enable [find comment="ISP-1"]</br>
:foreach i in=[/ip firewall connection find protocol~"tcp"] do={ /ip firewall connection remove $i }</br>
:foreach i in=[/ip firewall connection find protocol~"udp"] do={ /ip firewall connection remove $i }</br>
log warning ("ISP-1 IS UP")</br>
</br>
#when DOWN:
</br>
/ip route disable [find comment="ISP-1"]</br>
/ip route enable [find comment="ISP-2"]</br>
:foreach i in=[/ip firewall connection find protocol~"tcp"] do={ /ip firewall connection remove $i }</br>
:foreach i in=[/ip firewall connection find protocol~"udp"] do={ /ip firewall connection remove $i }</br>
log warning ("ISP-1 IS DOWN")</br>
</br>
#do some other settings from this instruction</br>
#https://настройка-микротик.укр/nastrojka-neskolkih-provajderov-na-mikrotik-balansirovka-i-avtopereklyuchenie/</br>
