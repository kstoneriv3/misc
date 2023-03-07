# import pkg   # ModuleNotFoundError: No module named 'pkg'
import module1
from sub_pkg1 import module2
from sub_pkg2 import module3
# from . import module1  # ImportError: attempted relative import with no known parent package

module2.abs_import_module1()
# module2.abs_import_pkg_module1()  # ModuleNotFoundError: No module named 'pkg'
# module2.rel_import_module1()  # ValueError: attempted relative import beyond top-level package
module3.abs_import_sub_pkg1_module2()
# module3.rel_import_sub_pkg1_module2()  # ValueError: attempted relative import beyond top-level package

### Append ../
import sys
sys.path.append("../")
import pkg  # Now it works as the path of pkg is in sys.path

module2.abs_import_module1()
module2.abs_import_pkg_module1()
# module2.rel_import_module1()  # ValueError: attempted relative import beyond top-level package
module3.abs_import_sub_pkg1_module2()
# module3.rel_import_sub_pkg1_module2()  # ValueError: attempted relative import beyond top-level package

### import module2 and module2 as submodules rather than top module
from pkg.sub_pkg1 import module2
from pkg.sub_pkg2 import module3

module2.abs_import_module1()
module2.abs_import_pkg_module1()
module2.rel_import_module1()  # now relative import can look at any files under pkg
module3.abs_import_sub_pkg1_module2()
module3.rel_import_sub_pkg1_module2()  # now relative import can look at any files under pkg
