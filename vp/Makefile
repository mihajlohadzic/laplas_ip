CC = "g++"
CXXFLAGS = -g -fno-omit-frame-pointer
PROJECT = main
SRC = $(wildcard *.cpp)
OBJ=$(SRC:.cpp=.o) 

LIBS = `pkg-config opencv4 --cflags --libs` -lsystemc

$(PROJECT) : $(OBJ)
	${CXX} ${CXXFLAGS} $^ -o $@ ${LIBS}
	
%.o : %.cpp
	${CXX} ${CXXFLAGS} -c $^ -o $@ ${LIBS}

profiling: 
	valgrind --tool=callgrind ./${PROJECT} ..data/oblici.pgm
clean:
	rm -f *.o all $(PROJECT) callgrind.*	
