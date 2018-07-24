CFLAGS := -pipe -Wall -Wextra
OS     := $(shell uname -s)
TARGET := libloop.a

.PHONY: all clean

ifdef M32
  CFLAGS  += -m32
  LDFLAGS += -m32
endif

ifdef DEBUG
  CFLAGS += -O0 -g
else
  CFLAGS += -O2 -DNDEBUG
  ifneq "$(OS)" "Darwin"
    LDFLAGS += -s
  endif
endif

ifeq "$(OS)" "Linux"
  CFLAGS += -DHAVE_EPOLL
endif

all: $(TARGET)

loop.o: loop.c loop.h
libloop.a: libloop.a(loop.o)

clean:
	rm -f *.o *.a

