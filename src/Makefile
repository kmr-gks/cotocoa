.PHONY: all install clean
.DEFAULT_GOAL := install

PREFIX=..
CC=mpiicc
FC=mpiifort
CFLAGS=-I.
LDFLAGS=-L.
LIBS=-lctca
F_LIBS=-lctca_f -lctca_mod

FILES = ctca ctca_f ctca_mod

OBJECTS = $(FILES:=.o)
TARGETS = $(FILES:%=lib%.a)

all: ${TARGETS} ${OBJECTS}

lib%.a: %.o
	ar rc $@ $^

%.o: %.c
	$(CC) $(CFLAGS) -c $^
%.o: %.f90
	$(FC) $(CFLAGS) -c $^

install: all
	/usr/bin/mkdir -p ${PREFIX}/lib
	/usr/bin/mkdir -p ${PREFIX}/include
	/bin/cp libctca.a libctca_f.a libctca_mod.a ${PREFIX}/lib
	/bin/cp ctca.h ctca.mod ${PREFIX}/include

clean:
	/bin/rm -f *.o *.mod ${TARGETS}
