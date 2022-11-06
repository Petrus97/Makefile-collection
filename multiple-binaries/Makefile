CC=gcc
CFLAGS=-g -Wall -Werror -Wpedantic
LDLIBS=-lm

SRC_DIR=./src
INC_DIR=./include
OBJ_DIR=./objs

SRCS=$(wildcard $(SRC_DIR)/*.c)
OBJS=$(patsubst $(SRC_DIR)/%.c, $(OBJ_DIR)/%.o, $(SRCS))

BINS := $(patsubst $(SRC_DIR)/%.c,%,$(SRCS))

#
# Compile each binary
#
all: prebuild $(BINS)

$(BINS): %: $(OBJ_DIR)/%.o
	$(CC) $(CFLAGS) -o $@ $^ -I$(INC_DIR) $(LDLIBS)

$(OBJS): $(OBJ_DIR)/%.o:$(SRC_DIR)/%.c
	$(CC) $(CFLAGS) -c $< -o $@ -I$(INC_DIR)

#
# Add the operations to do before start the compilation
#
prebuild:
	mkdir -p $(OBJ_DIR)

clean:
	rm -rf $(BINS) $(OBJ_DIR)/*