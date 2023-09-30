# CMake

# build makefile
 on windows to build makefile for project, execute following command in directory where CMakeLists.txt is present
 following command will create makefile for project in build/ directory 
on windows 'cmake -G "MinGW Makefiles" -B build -S .'      on linux do 'cmake -B build -S .'
# build executables 
following command will execute makefile and build the executables for client and server
On both linux/windows do 'cmake --build build'   or  goto build/  on linux do 'make', on windows do 'mingw32-make'


# makefile for windows , if cmake does not works
CC = g++
CFLAGS = -std=c++11
LDFLAGS = -lws2_32
OBJ_DIR = obj

all: $(OBJ_DIR) server.exe client.exe

$(OBJ_DIR):
	mkdir $(OBJ_DIR)

$(OBJ_DIR)/server.exe: server.cpp
	$(CC) $(CFLAGS) -o $@ $< $(LDFLAGS)

$(OBJ_DIR)/client.exe: client.cpp
	$(CC) $(CFLAGS) -o $@ $< $(LDFLAGS)


clean:
	rm -rf $(OBJ_DIR) server.exe client.exe

# make ends here 