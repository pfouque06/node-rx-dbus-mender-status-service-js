# dbus-next example service

Compile and run with:

```
# system configuration
cp org.test.name /usr/share/dbus-1/system-services
cp org.test.name.conf /etc/dbus-1/system.d

# npm install
yarn
yarn build
yarn go
```

Set a property:

```
gdbus call --session --dest org.test.name --object-path /org/test/path \
  --method org.freedesktop.DBus.Properties.Set \
  'org.test.iface' 'MapProperty' "<{'foo':<'bar'>}>"
```

Get a property:

```
gdbus call --session --dest org.test.name --object-path /org/test/path \
  --method org.freedesktop.DBus.Properties.Get \
  'org.test.iface' 'MapProperty'
```


Get .....
```
dbus-send --system --type=method_call --print-reply=literal --dest=org.test.name /org/test/path org.test.iface.Get
```


monitor d-bus:
```
dbus-monitor --system "type='signal', sender='org.test.name', interface='org.test.iface'"
```