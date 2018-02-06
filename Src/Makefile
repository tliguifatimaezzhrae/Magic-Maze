CXX      = g++

.DEFAULT_GOAL := all

SOURCES = 
SOURCES += melangeur.cpp

OBJECTS = $(SOURCES:.cpp=.o)

CXXFLAGS  += -g -Wall -std=c++11 -pedantic
LDFLAGS +=

$(OBJECTS) : %.o : %.cpp
	$(CXX) -MMD $(CXXFLAGS) -c $< -o $@

CLEAN_OBJECTS = $(OBJECTS)
TARGETS = 

########## test_melangeur ##########

MELANGEUR_SOURCES = test_melangeur.cpp
MELANGEUR_OBJECTS = $(MELANGEUR_SOURCES:.cpp=.o)

test_melangeur : $(MELANGEUR_OBJECTS) $(OBJECTS) $(HEADERS)
	$(CXX) $(MELANGEUR_OBJECTS) $(OBJECTS) -o $@ $(LDFLAGS)
	
$(MELANGEUR_OBJECTS): %.o : %.cpp
	$(CXX) -MMD $(CXXFLAGS) -c $< -o $@

all : test_melangeur
TARGETS += test_melangeur
CLEAN_OBJECTS += $(MELANGEUR_OBJECTS)

########## cleanup ##########
DEPS = $(CLEAN_OBJECTS:.o=.d)

clean:
	@rm -f $(DEPS) $(TARGETS) $(CLEAN_OBJECTS)

-include $(DEPS)
