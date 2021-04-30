# iwndebug

## What is it for?

_iwndebug_ is a friendly tool to toggle debugging levels of the iwn(4) driver.
It leverages the sysctl(8) framework using the debug oid of the driver. You need
to build your kernel with `options IWN_DEBUG` in order to see the debugging
messages of the driver on the console or via syslog(3).

## How to build

It needs to be build from inside the
[freebsd-src](https://github.com/freebsd/freebsd-src.git) sources.

* Clone sources

```
git clone --depth 1 -b main https://git.freebsd.org/src.git /usr/src
git clone https://github.com/sbz/iwndebug.git
cp -r iwndebug/tools /usr/src/tools/
```

* Build

```
cd /usr/src/tools/tools/iwn
make
make install
```

iwn(4) is an old driver and does not spark interests and attention anymore
compare to more recent hardware but I'm still using an old thinkpad with it :)

### How to use

You need super user (root or sudo) privileges to use it as it's installed under
`/usr/local/sbin` folder.

```
iwndebug -h
```

### Enable logging trace (can disable with -)

```
iwndebug +trace
```

### Disable every debug messages

```
iwndebug none
```

### List all supported debug levels 

```
iwndebug -?
```

### Redirect log messages from console

By default log messages are displayed on the console via `/dev/console`, you can
configure syslog(3) daemon to print driver messages from the kernel in the
`/var/log/debug.log` file using the following:

```
# echo "kern.debug       /var/log/debug.log" > /etc/syslog.d/debug.conf
# service restart syslogd
# tail -n 0 -f /var/log/debug.log
```
