ROOT_DIR = ../../..
PBCPP_DIR = $(ROOT_DIR)/..
include $(ROOT_DIR)/common.mk

SOURCES = $(wildcard *.cpp) 
OBJECTS = $(SOURCES:.cpp=.o)
EXECS = $(SOURCES:.cpp=)


all: $(SOURCES) $(OBJECTS) $(EXECS)

$(EXECS): % : %.o
	$(CXX) $(CCOPTS) $< $(GTEST_MAINA) -o $@ $(LDFLAGS)

.cpp.o:
	$(CXX) $(CCOPTS) -c $< -o $@

gtest: $(EXECS)
	@(for exe in $(EXECS); do echo "Running $$exe"; ./$$exe --gtest_output=$(ROOT_DIR)/$$exe.xml; done;)

clean:
	@rm -f $(OBJECTS) $(EXECS)
