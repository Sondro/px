
CXXFLAGS=-std=c++11 -pedantic -g -O2\
	-Wall \
	-Wcast-align \
	-Wcast-qual \
	-Wctor-dtor-privacy \
	-Wdisabled-optimization \
	-Wdouble-promotion \
	-Werror \
	-Wextra \
	-Wformat=2 \
	-Winit-self \
	-Wmissing-include-dirs \
	-Wno-unused\
	-Wold-style-cast \
	-Woverloaded-virtual \
	-Wredundant-decls \
	-Wshadow \
	-Wsign-conversion \
	-Wsign-promo \
	-Wstrict-overflow=5 \
	-Wswitch-default \
	-Wundef \

UNAME_S := $(shell uname -s)


ifeq ($(UNAME_S),Linux)
  LDFLAGS += -lpthread
  ifeq ($(config),tsan)
    LDFLAGS += -ltsan
    CXXFLAGS += -fsanitize=thread -pie -fPIE
  endif
endif

px_sched_examples = px_sched_example1 px_sched_example2 px_sched_example3 px_sched_example4 px_sched_example5 px_sched_example6 px_sched_example7
all: $(px_sched_examples)

$(px_sched_examples): %: %.cpp ../px_sched.h
	$(CXX) $(CXXFLAGS) -o $@ $(LDFLAGS) $<

.PHONY: clean tests
clean:
	rm -f $(px_sched_examples)

tests: $(px_sched_examples)
	./px_sched_example1 
	./px_sched_example2 
	./px_sched_example3 
	./px_sched_example4 
	./px_sched_example5 
	./px_sched_example6 
	./px_sched_example7
	@echo "ALL px_sched_examples executed"
