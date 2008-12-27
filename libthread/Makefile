all:
		g++ -g3 -I./include/ -fPIC -g -c -Wall \
		Thread.cpp
		g++ -g3 -I./include/ -fPIC -g -c -Wall \
		ThreadException.cpp
		g++ -g3 -shared -Wl,-soname,libthread.so.1 -o ./libthread.so.1.0.0 \
		Thread.o ThreadException.o -lc -lpthread

clean:
		@if [ -f Thread.o ]; then rm Thread.o; fi
		@if [ -f ThreadException.o ]; then rm ThreadException.o; fi
		@if [ -f libthread.so.1.0.0 ]; then rm libthread.so.1.0.0; fi
		@if [ -f test ]; then rm test; fi

install: all
		cp ./libthread.so.1.0.0 /usr/lib/
		ldconfig -v

uninstall:

test:
		g++ -I./include -combine Thread.cpp TestRunnable.cpp ThreadException.cpp \
		main.cpp -o test -lpthread
		
.PHONY: all clean install uninstall test