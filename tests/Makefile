# Add your test source files here:
SOURCES = $(wildcard *.c)

# Point this variable to the libsemanage source directory you want to test:
TESTSRC=../src

# Add the required external object files here:
LIBS = ../src/libsemanage.a /usr/lib/libselinux.a /usr/lib/libsepol.a

###########################################################################

EXECUTABLE = libsemanage-tests
CC = gcc
CFLAGS = -c -g -o0 -Wall -W -Wundef -Wmissing-noreturn -Wmissing-format-attribute -Wno-unused-parameter
INCLUDE = -I$(TESTSRC) -I$(TESTSRC)/../include
LDFLAGS = -lcunit -lustr -lbz2
OBJECTS = $(SOURCES:.c=.o) 

all: $(EXECUTABLE) 

$(EXECUTABLE): $(OBJECTS) 
	$(CC) $(OBJECTS) $(LIBS) $(LDFLAGS) -o $@

%.o: %.c
	$(CC) $(CFLAGS) $(INCLUDE) $*.c -o $*.o

clean distclean: 
	rm -rf $(OBJECTS) $(EXECUTABLE)

test: all 
	./$(EXECUTABLE)

