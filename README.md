# CMake


# on windows to build cmake project, execute following command in directory where CMakeLists.txt is present
# following command will create makefile for project in build/ directory 
cmake -G "MinGW Makefiles" -B build -S .
# following command will execute makefile and build the executables for client and server
cmake --build build


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

server.exe: $(OBJ_DIR)/server.exe
#	copy /Y $< $@

client.exe: $(OBJ_DIR)/client.exe
#	copy /Y $< $@

clean:
	rm -rf $(OBJ_DIR) server.exe client.exe

# make ends here 