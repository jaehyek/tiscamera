#
# Copyright 2016 The Imaging Source Europe GmbH
#
# Licensed under the Apache License, Version 2.0 (the "License");
# you may not use this file except in compliance with the License.
# You may obtain a copy of the License at
#
# http://www.apache.org/licenses/LICENSE-2.0
#
# Unless required by applicable law or agreed to in writing, software
# distributed under the License is distributed on an "AS IS" BASIS,
# WITHOUT WARRANTIES OR CONDITIONS OF ANY KIND, either express or implied.
# See the License for the specific language governing permissions and
# limitations under the License.



LIBS:=$(shell pkg-config gstreamer-1.0 --libs)
LIBS:=$(shell pkg-config gstreamer-video-1.0 --libs)
LIBS+=$(shell pkg-config gtk+-3.0 --libs)
LIBS+=$(shell pkg-config gobject-introspection-1.0 --libs)
LIBS+=$(shell pkg-config tcam --libs)

CFLAGS:=$(shell pkg-config gstreamer-1.0 --cflags)
CFLAGS:=$(shell pkg-config gstreamer-video-1.0 --cflags)
CFLAGS+=$(shell pkg-config gtk+-3.0 --cflags)
CFLAGS+=$(shell pkg-config gobject-introspection-1.0 --cflags)
CFLAGS+=$(shell pkg-config tcam --cflags)


.PHONY: all clean

EXECS = 00-list-devices 01-list-properties 02-set-properties 03-live-stream 04-list-formats 05-set-format 06-softwaretrigger 07-appsink 08-save-stream 09-device-lost


all: $(EXECS)


$(EXECS): %: %.c
	$(CC) -g -DGST_DISABLE_DEPRECATED -O0 $(CFLAGS) -o $@ $< $(LIBS)

clean:
	$(RM) *.o
	$(RM) $(EXECS)
