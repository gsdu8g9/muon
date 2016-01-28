# muon #

[![Release](https://img.shields.io/github/release/XiaoxiaoPu/muon.svg)](https://github.com/XiaoxiaoPu/muon/releases/latest)
[![License](https://img.shields.io/badge/license-GPL%203-blue.svg)](https://www.gnu.org/licenses/gpl.html)
[![Build Status](https://ci.xiaoxiao.im/buildStatus/icon?job=muon)](https://ci.xiaoxiao.im/job/muon)

A fast, obscured stateless VPN

## Features ##

1. Stateless
2. Perform naïve obfuscation by compression, padding and delayed transmission
3. Frequent port hopping to escape traffic monitoring


## Dependencies ##

1. [libmill](http://libmill.org/)


## Build ##

### 1. Linux ###

install GNU Autotools, libmill according to your distribution, then:

```bash
autoreconf -if
./configure --prefix=/usr --sysconfdir=/etc
make
sudo make install
```

### 2. OS X ###

install homebrew first, then:

```bash
brew install --HEAD https://github.com/XiaoxiaoPu/muon/raw/master/contrib/homebrew/muon.rb
```

### 3. Cross compile ###

setup cross compile tool chain:

```bash
export PATH="$PATH:/pato/to/cross/compile/toolchain/"
```

build:

```bash
# build libmill
git clone https://github.com/sustrik/libmill.git
pushd libmill
./autogen.sh
./configure --host=arm-unknown-linux-gnueabihf
make
popd
# build muon
autoreconf -if
export CPPFLAGS=-I$(pwd)/libmill
export LDFLAGS=-L$(pwd)/libmill
./configure --host=arm-unknown-linux-gnueabihf \
    --prefix=/usr --sysconfdir=/etc
make
```


## Usage ##

See man:muon(8).


## License ##

Copyright (C) 2014 - 2016, Xiaoxiao <i@xiaoxiao.im>

This program is free software: you can redistribute it and/or modify
it under the terms of the GNU General Public License as published by
the Free Software Foundation, either version 3 of the License, or
(at your option) any later version.

This program is distributed in the hope that it will be useful,
but WITHOUT ANY WARRANTY; without even the implied warranty of
MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
GNU General Public License for more details.

You should have received a copy of the GNU General Public License
along with this program. If not, see <http://www.gnu.org/licenses/>.
