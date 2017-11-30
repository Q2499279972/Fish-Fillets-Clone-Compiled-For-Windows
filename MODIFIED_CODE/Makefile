#----------------------------------------------
#
#     Makefile pro ff-clone
#
#-----------------------------------------------

BINDIR = .
DATADIR = .

#-----------------------------------------------

CC = gcc
INCLUDE = -I. $(shell pkg-config --cflags lua 2>/dev/null || pkg-config --cflags lua5.1 2>/dev/null || echo "")
OBJ = main.o loop.o warning.o window.o X.o draw.o gener.o layers.o script.o levelscript.o object.o rules.o moves.o gmoves.o keyboard.o imgsave.o directories.o menudraw.o menuevents.o menuscript.o gsaves.o infowindow.o
LIB =  -lX11 -lcairo $(LDFLAGS)
PROGNAME = ff-clone

all: $(PROGNAME)

directories.o: directories.c
	$(CC) $(INCLUDE) -g -Wall -c -o directories.o directories.c -DDATADIR="\"$(DATADIR)\""

.c.o:
	$(CC) $(INCLUDE) -g -Wall -c -o $*.o $<

$(PROGNAME): $(OBJ)
	$(CC) $(INCLUDE) $(OBJ) ../lua-5.1.5/src/liblua.a $(LIB) -o $@

clean:
	rm -rf *.o $(PROGNAME)

install: $(PROGNAME)
	install -s $(PROGNAME) $(BINDIR)/
	mkdir -p $(DATADIR)
	cp -r data/* $(DATADIR)/

uninstall:
	rm $(BINDIR)/$(PROGNAME)
	rm -r $(DATADIR)
