CFLAGS = -Wall -Wextra -DLOG_USE_COLOR -DHLOG=$(LOG)
objects = $(wildcard *.c) ../cJSON/cJSON.c

ifeq ($(ARCH), arm64)
	CC := aarch64-linux-gnu-gcc
else ifeq ($(ARCH), riscv)
	CC := riscv64-linux-gnu-gcc
else ifeq ($(ARCH), loongarch)
	CC := loongarch64-unknown-linux-gnu-gcc
	CFLAGS += -DLOONGARCH64 -static
else
	CC := gcc
endif

.PHONY: all clean
all: 
	$(CC) $(CFLAGS) -g -o hvisor $(objects) -I./include/ -I../include/ -I../cJSON/ -lpthread

asm:
	$(CC) $(CFLAGS) -S htool.s $(objects) -I../driver/ -I./includes/ -lpthread
clean:
	rm -f hvisor