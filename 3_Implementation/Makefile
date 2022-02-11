#Target : Dependencies
#<TAB>commands
PROJ_FOL = M1_PhoneBookManager_Utility
PROJ_NAME = PhoneBook_manager
TEST_PROJ_NAME = test_$(PROJ_NAME)
TEST_PROJ_NAME = test_$(PROJ_NAME)
BUILD_DIR = Build
SRC = src/demo.c
TEST_SRC = test/test_demo.c\
unity/unity.c

TEST_OUTPUT = $(BUILD)/test_demo.out

BUILD_DIR = Build

unity/unity.c

INC = -I inc -I unity

ifdef OS
   RM = del /q
   FixPath = $(subst /,\,$1)
   EXEC = exe
else
   ifeq ($(shell uname), Linux)
      RM = rm -rf
      FixPath = $1
	  EXEC = out
   endif
endif

.PHONY : all test coverage run clean doc

all:$(BUILD_DIR)
	gcc main1.c $(SRC) $(INC) -o $(call FixPath,$(BUILD_DIR)/$(PROJ_NAME).$(EXEC)) -lm 

run: all
	$(call FixPath,$(BUILD_DIR)/$(PROJ_NAME).$(EXEC))

test: $(SRC) $(TEST_SRC)
	gcc $^ $(INC) -o $(call FixPath,$(BUILD_DIR)/$(TEST_PROJ_NAME).$(EXEC)) -lm
	$(call FixPath,$(BUILD_DIR)/$(TEST_PROJ_NAME).$(EXEC))


coverageCheck:$(BUILD)
	gcc -fprofile-arcs -ftest-coverage -fPIC -O0 $(SRC) $(TEST_SRC) $(INC) -o $(BUILD_DIR)$(TEST_OUTPUT)
	./$(BUILD_DIR)/$(TEST_OUTPUT)

doc:
	make -C doc
$(BUILD_DIR):
	mkdir $(BUILD_DIR)

clean:
	$(RM) $(call FixPath,$(BUILD_DIR)/*)
	make clean -C doc
	rmdir $(BUILD_DIR) doc/html