CC=g++
CFLAGS= -std=c++11 -g -O0 -Wall
TARGET=$(patsubst %.cpp, %.t, $(wildcard *.cpp))  
OBJS=$(patsubst %, %.o, $(TARGET))
LINK=-L ../libgo  -L /usr/lib64 -lboost_coroutine \
	-lboost_thread -lboost_system -lboost_context -lpthread -lcurl

all : $(TARGET)

%.t: %.o
	@$(CC) $(CFLAGS) $^ -o $@ ${LINK} -L../libgo -llibgo -ldl
	@echo "LD $@"

.cpp.o:
	@$(CC) $(CFLAGS) -c $^ -I../libgo -I../libgo/linux -o $@
	@echo "MK $@"

.PHONY: clean

clean:
	rm *.o *.t -f
