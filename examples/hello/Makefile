
include nuttx-export-10.4.0/scripts/Make.defs

ARCHINCLUDES += -isystem nuttx-export-10.4.0/include

CFLAGS = $(ARCHCFLAGS) $(ARCHWARNINGS) $(ARCHOPTIMIZATION) $(ARCHCPUFLAGS) $(ARCHINCLUDES) $(ARCHDEFINES) $(EXTRADEFINES)
CELFFLAGS = $(CFLAGS) -mtext-section-literals

# This might change in a different environment

OBJEXT ?= .o

# This is the generated ELF program

BIN = hello

# These are the sources files that we use

SRCS = hello.c
OBJS = $(SRCS:.c=$(OBJEXT))

# Build targets

all: $(BIN)
.PHONY: clean

$(OBJS): %$(OBJEXT): %.c
	$(Q) $(CC) -c $(CELFFLAGS) $< -o $@

$(BIN): $(OBJS)
	$(LD) $(LDFLAGS) $(LDELFFLAGS) -o $@ $^

clean:
	rm -f $(BIN)
	rm -f *.o
