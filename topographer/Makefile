CC = g++

CFLAGS_COMMON = -fopenmp -m64 -std=c++17 -fPIC
CFLAGS_DEBUG = $(CFLAGS_COMMON) -O0 -Wall
CFLAGS_RELEASE = $(CFLAGS_COMMON) -Os -w
CFLAGS = $(CFLAGS_RELEASE)

PROJECT_NAME = topographer
LIBS = -lstdc++fs

PROJECT_INCLUDE_DIR = include
PROJECT_SOURCE_DIR = src
PROJECT_OBJECTS_DIR = objects
PROJECT_BUILD_DIR = build
PROJECT_SOURCES = $(wildcard $(PROJECT_SOURCE_DIR)/*.cpp)
PROJECT_OBJECTS = $(patsubst $(PROJECT_SOURCE_DIR)/%.cpp, $(PROJECT_OBJECTS_DIR)/%.o, $(PROJECT_SOURCES))

MKDIR = \mkdir -p
RM = \rm -f

all: folders build

folders:
	$(MKDIR) $(PROJECT_BUILD_DIR)
	$(MKDIR) $(PROJECT_OBJECTS_DIR)

$(PROJECT_OBJECTS_DIR)/%.o: $(PROJECT_SOURCE_DIR)/%.cpp
	$(CC) $(CFLAGS) -c -I$(PROJECT_INCLUDE_DIR) -o $@ $<

build: $(PROJECT_OBJECTS)
	$(CC) $(CFLAGS) -I$(PROJECT_INCLUDE_DIR) -o $(PROJECT_BUILD_DIR)/${PROJECT_NAME}.run $(PROJECT_SOURCES) $(LIBS)

clean:
	$(RM) -r $(PROJECT_BUILD_DIR)
	$(RM) -r $(PROJECT_OBJECTS_DIR)
