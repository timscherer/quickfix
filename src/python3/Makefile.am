pythondir = $(PYTHON3_SITE_PACKAGES)
python_LTLIBRARIES = _quickfix.la
_quickfix_la_SOURCES = \
	QuickfixPython.cpp

python_DATA = quickfix.py quickfix40.py quickfix41.py quickfix42.py quickfix43.py quickfix44.py quickfix50.py quickfix50sp1.py quickfix50sp2.py quickfixt11.py

CXXFLAGS:=$(filter-out -Wall,$(CXXFLAGS))
_quickfix_la_CXXFLAGS = -DPYTHON_MAJOR_VERSION=3 -Wno-unknown-warning-option -Wno-deprecated-declarations -Wno-unused-variable -Wno-maybe-uninitialized -Wno-misleading-indentation -Wno-terminate -Wno-unused-label -Wno-inconsistent-missing-override
_quickfix_la_LDFLAGS = -version-info 14:0:0 -module
_quickfix_la_LIBADD = $(top_builddir)/src/C++/libquickfix.la 

AM_CPPFLAGS = $(PYTHON3_CFLAGS) -I. -I.. -I../.. -I../C++ -I../swig

local_python_src=$(top_builddir)/src/python3
local_python_lib=$(top_builddir)/lib/python3

all-local: $(python_LTLIBRARIES)
	rm -rf $(local_python_lib)
	mkdir -p $(local_python_lib)
	ln -sf $(local_python_src)/.libs/_quickfix* $(local_python_lib)
	ln -sf $(local_python_src)/*.py $(local_python_lib)
	unlink spec
	ln -sf $(top_builddir)/spec spec

clean-local:
	rm -rf $(local_python_lib)

TESTS = test.sh
