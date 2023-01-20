192.168.1.34

echo 'export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre' >> ~/.bashrc
echo 'export JAVA_HOME=/usr/lib/jvm/java-8-openjdk-amd64/jre' >> ~/.bashrc

wget https://nexus.opendaylight.org/content/repositories/opendaylight.release/org/opendaylight/integration/karaf/0.8.4/karaf-0.8.4.zip https://nexus.opendaylight.org/content/repositories/opendaylight.release/org/opendaylight/integration/
karaf/0.8.4/karaf-0.8.4.zip


sudo unzip /usr/local/karaf/karaf-0.8.4.zip -d /usr/local/karaf/

sudo update-alternatives --install /usr/bin/karaf karaf /usr/local/karaf/karaf-0.8.4/bin/karaf 1 update-alternatives: using /usr/local/karaf/karaf-0.8.4/bin/karaf to provide /usr/bin/karaf (karaf) in auto mode




## Ejecutar opendaylight
```
sudo -E karaf
```


## instalar para ver en el navegador:

```
feature:install odl-restconf-all odl-l2switch-switch odl-mdsal-all features-dlux features-dluxapps
```

## Navegar

http://192.168.1.34:8181/index.html#/topology


## Crear una topología remota
```
sudo mn --topo linear,3 --mac --controller=remote,ip=192.168.1.34,port=6633 --switch ovs,protocols=OpenFlow13