# Copyright (C) 2015 PSP2SDK Project
#
# This program is free software: you can redistribute it and/or modify
# it under the terms of the GNU Lesser General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU Lesser General Public License for more details.
#
# You should have received a copy of the GNU Lesser General Public License
# along with this program.  If not, see <http://www.gnu.org/licenses/>.

PREFIX = _SceNpManager-0001_
ENTRIES_PREFIX = $(PREFIX)F00_

NIDS = 0x04d9f484 0x19e40ae1 0x3b0ae9a9 0x3c94b4b4 	\
	0x43dc48a1 0x44239c35 0x54060df6 0x60c575b1 	\
	0xaf0073b2 0xd9e6e56c 0xfe835967 

ENTRIES = $(addsuffix .o,$(addprefix $(ENTRIES_PREFIX),$(subst 0x,,$(NIDS))))

lib_LIBRARIES = libSceNpManager_stub.a
libSceNpManager_stub_a_SOURCES = SceNpManager_stub.S 
am_libSceNpManager_stub_a_OBJECTS =	\
	$(PREFIX)head.o $(PREFIX)NIDS.o $(ENTRIES)

$(PREFIX)head.o: $(libSceNpManager_stub_a_SOURCES)
	$(COMPILE) -DHEAD $< -c -o $@

$(PREFIX)NIDS.o: $(libSceNpManager_stub_a_SOURCES)
	$(COMPILE) -DNIDS $< -c -o $@

$(ENTRIES): $(libSceNpManager_stub_a_SOURCES)
	$(COMPILE) -DFUNC=$(subst $(ENTRIES_PREFIX),0x,$*) $< -c -o $@