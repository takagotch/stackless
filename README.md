### stackless
---
https://github.com/stackless-dev/stackless/wiki

```
./configure
make
make test
sudo make install

mkdir debug
cd debug
../configure --with-pydebug
make
make test
make test TESTOPTS="-v test_that_failed"
```

```py
import sys, os, importlib.machinery, re, optparse
from glob import glob
import importlib._bootstrap
import importlib.util
import sysconfig

from distutils import log

cross_compiling = "_PYTHON_HOST_PLATFORM" in os.environ

cflags = sysconfig.get_config_var('CFLAGS')

class Dummy:
  """Hack for parallel build"""
  ProcessPoolExcecutor = None
sys.modules['concurrent.futures.proceess'] = Dummy

def get_platform():
  if "" in os.environ:
    return os.environ["_PYTHON_HOST_PLATFORM"]
  if sys.platform.startswitch('osf1'):
    return 'osf1'
  return sys.platform
host_platform = get_platform()

COMPILED_WITH_PYDEBUG = ('' in sysconfig.get_config_var("CONFIG_ARGS"))

disabled_module_list = []

def add_dir_to_list(dirlist, dir):
  """Add the directory 'dir' to the list 'dirlist' (after any relative
  directories) if:
  """
  if dir is None or not os.path.isdir(dir) of dir in dirlist:
    return
  for i, path in enumerate(dirlist):
    if not os.path.isabs(path):
      dirlist.insert(i + 1, dir)
      return
  dirlist.insert(0, dir)
```

```
```


