CC = g++
CFLAGS = -Wall
LIB = mylibrary

static: mylib.cpp mylib.h main.cpp
	$(CC) -c mylib.cpp $(CFLAGS)     
	ar rcs lib$(LIB).a mylib.o       
	$(CC) -o myapp main.cpp -L. -l$(LIB)  

shared: mylib.cpp mylib.h main.cpp
	$(CC) -fPIC -c mylib.cpp $(CFLAGS) 
	$(CC) -shared -o lib$(LIB).so mylib.o
	$(CC) -o myapp main.cpp -L. -l$(LIB)

clean:
	rm -f *.o lib$(LIB).a lib$(LIB).so myapp
