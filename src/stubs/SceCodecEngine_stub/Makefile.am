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

PREFIX = _SceCodecEngine-0001_
ENTRIES_PREFIX = $(PREFIX)F00_

NIDS = 0x1a3a53e5 0x6a31831d 0x95ea3b3e 0xf0b4c892 

ENTRIES = $(addsuffix .o,$(addprefix $(ENTRIES_PREFIX),$(subst 0x,,$(NIDS))))

lib_LIBRARIES = libSceCodecEngine_stub.a
libSceCodecEngine_stub_a_SOURCES = SceCodecEngineUser_stub.S 
am_libSceCodecEngine_stub_a_OBJECTS =	\
	$(PREFIX)head.o $(PREFIX)NIDS.o $(ENTRIES)

$(PREFIX)head.o: $(libSceCodecEngine_stub_a_SOURCES)
	$(COMPILE) -DHEAD $< -c -o $@

$(PREFIX)NIDS.o: $(libSceCodecEngine_stub_a_SOURCES)
	$(COMPILE) -DNIDS $< -c -o $@

$(ENTRIES): $(libSceCodecEngine_stub_a_SOURCES)
	$(COMPILE) -DFUNC=$(subst $(ENTRIES_PREFIX),0x,$*) $< -c -o $@