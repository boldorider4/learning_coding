CC=/usr/bin/g++-6
CCFLAGS=-Wall -std=c++11

SRC=./src
INCLUDE=./include

CCINCLUDE=-I./$(INCLUDE) -I./src

LDFLAGS=-lstdc++fs

ifeq ($(DEBUG),1)
        CCFLAGS+=-g -O0
endif

all: occi occ

occi: main_occi.o BasicOccurrenceCounter.o FastOccurrenceCounter.o InteractiveConsole.o CommonOccurrenceCounter.o
	@ $(CC) $(CCFLAGS) $(CCINCLUDE) $(LDFLAGS) -o $@ $^

occ: main_occ.o BasicOccurrenceCounter.o FastOccurrenceCounter.o InteractiveConsole.o CommonOccurrenceCounter.o
	@ $(CC) $(CCFLAGS) $(CCINCLUDE) $(LDFLAGS) -o $@ $^

%.o: $(SRC)/%.cpp
	@ $(CC) -c $(CCFLAGS) $(CCINCLUDE) -o $@ $<

main_occi.o: $(INCLUDE)/errorCode.h $(INCLUDE)/IOccurrenceCounter.h $(INCLUDE)/InteractiveConsole.h $(INCLUDE)/FastOccurrenceCounter.h
main_occ.o: $(INCLUDE)/errorCode.h $(INCLUDE)/IOccurrenceCounter.h $(INCLUDE)/InteractiveConsole.h $(INCLUDE)/BasicOccurrenceCounter.h
FastOccurrenceCounter.o: $(INCLUDE)/IOccurrenceCounter.h $(INCLUDE)/FastOccurrenceCounter.h $(INCLUDE)/BasicOccurrenceCounter.h $(INCLUDE)/HashTable.h
BasicOccurrenceCounter.o: $(INCLUDE)/IOccurrenceCounter.h $(INCLUDE)/BasicOccurrenceCounter.h $(INCLUDE)/errorCode.h
InteractiveConsole.o: $(INCLUDE)/InteractiveConsole.h $(INCLUDE)/errorCode.h

clean:
	@ rm -rf occ* *.o *~ *.dSYM $(INCLUDE)/*~ $(SRC)/*~
