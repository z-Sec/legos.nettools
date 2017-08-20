# legos.net-tools

Provide a set of networking tools which operate from chat.

## Installation

`pip3 install legos.nettools` will grab this package and the Legobot required to run it.

## Example

```python3
import threading

from Legobot.Connectors.IRC import IRC
from Legobot.Lego import Lego
from Legobot.Legos.Help import Help

from legos.nettools import LegoNettools

# Initialize lock and baseplate
lock = threading.Lock()
baseplate = Lego.start(None, lock)
baseplate_proxy = baseplate.proxy()

# Connect to a chat medium
baseplate_proxy.add_child(IRC,
                          channels=['#test'],
                          nickname='bot',
                          server='irc.foo.bar',
                          port=6697,
                          use_ssl=True)

# Add children
baseplate_proxy.add_child(Help)
baseplate_proxy.add_child(LegoNettools)

```

### Commands

The nettools Lego could be triggered by various prefix.

- [x] Whois
- [ ] Nslookup
- [ ] DNS
- [ ] Trace
- [ ] Ping
- [ ] SSLscan
- [X] IP geo

#### Whois

` !whois {--getStatus | --getEmails | --getRegistrar | --getNS} {target}`

#### Geolocalisation

` !geoloc {target}`

## Contributing

As always, pull requests and issues are welcome.
