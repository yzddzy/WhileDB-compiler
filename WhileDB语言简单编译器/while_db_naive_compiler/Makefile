lexer.h: lang.l
	 flex lang.l

lexer.c: lang.l
	 flex lang.l

parser.c: lang.y
	 bison -o parser.c -d -v lang.y

parser.h: lang.y
	 bison -o parser.c -d -v lang.y

lang.o: lang.c lang.h
	 gcc -c lang.c

L1.o: L1.c lang.h L1.h
	 gcc -c L1.c

parser.o: parser.c parser.h lexer.h lang.h
	 gcc -c parser.c

lexer.o: lexer.c lexer.h parser.h lang.h
	 gcc -c lexer.c

lib.o: lib.h lib.c
	 gcc -c lib.c

main.o: main.c lexer.h parser.h lang.h L1.h lib.h
	 gcc -c main.c

main: lib.o lang.o parser.o lexer.o L1.o main.o 
	 gcc lib.o lang.o L1.o parser.o lexer.o main.o 	-o main

all: main

clean:
	 rm -f lexer.h lexer.c parser.h parser.c *.o

%.c: %.y

%.c: %.l

.DEFAULT_GOAL := all