# Copyright (C) 2015 PSP2SDK Project
#
# This Source Code Form is subject to the terms of the Mozilla Public
# License, v. 2.0. If a copy of the MPL was not distributed with this
# file, You can obtain one at http://mozilla.org/MPL/2.0/.

PREFIX = _SceSha512t-0001_
ENTRIES_PREFIX = $(PREFIX)F00_

NIDS = 0x00e52720 0x66425db6 0x79065bb2 0xc5359df8

ENTRIES = $(addsuffix .o,$(addprefix $(ENTRIES_PREFIX),$(subst 0x,,$(NIDS))))

lib_LIBRARIES = libSceSha512t_stub.a
libSceSha512t_stub_a_SOURCES = SceSha512t_stub.S
am_libSceSha512t_stub_a_OBJECTS =	\
	$(PREFIX)head.o $(PREFIX)NIDS.o $(ENTRIES)

$(PREFIX)head.o: $(libSceSha512t_stub_a_SOURCES)
	$(COMPILE) -DHEAD $< -c -o $@

$(PREFIX)NIDS.o: $(libSceSha512t_stub_a_SOURCES)
	$(COMPILE) -DNIDS $< -c -o $@

$(ENTRIES): $(libSceSha512t_stub_a_SOURCES)
	$(COMPILE) -DFUNC=$(subst $(ENTRIES_PREFIX),0x,$*) $< -c -o $@
