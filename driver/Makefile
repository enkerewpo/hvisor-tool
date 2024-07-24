obj-m += hvisor.o

EXTRA_CFLAGS += "

ifeq ($(ARCH), arm64)
	COMPILE := aarch64-none-linux-gnu-
else ifeq ($(ARCH), riscv)
	COMPILE := riscv64-unknown-linux-gnu-
else ifeq ($(ARCH), loongarch)
	COMPILE := loongarch64-unknown-linux-gnu-
	EXTRA_CFLAGS += -DLOONGARCH64
else
	COMPILE := 
endif

EXTRA_CFLAGS += -I$(PWD)/include
EXTRA_CFLAGS += "

.PHONY: all clean
all:
	make ARCH=$(ARCH) CROSS_COMPILE=$(COMPILE) -C $(KDIR) M=$(shell pwd) EXTRA_CFLAGS=$(EXTRA_CFLAGS) modules
 
clean:
	make -C $(KDIR) M=$(shell pwd) clean