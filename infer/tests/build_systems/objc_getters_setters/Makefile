# Copyright (c) 2017-present, Facebook, Inc.
#
# This source code is licensed under the MIT license found in the
# LICENSE file in the root directory of this source tree.

TESTS_DIR = ../..
ROOT_DIR = $(TESTS_DIR)/../..
CODETOANALYZE_DIR = ../codetoanalyze/objc_getters_setters

ANALYZER = checkers
SOURCES = $(CODETOANALYZE_DIR)/A.m $(CODETOANALYZE_DIR)/B.m
OBJECTS = $(CODETOANALYZE_DIR)/A.o $(CODETOANALYZE_DIR)/B.o
INFER_OPTIONS = --biabduction-only --report-custom-error --developer-mode --project-root $(TESTS_DIR)
INFERPRINT_OPTIONS = --project-root $(TESTS_DIR) --issues-tests

include $(TESTS_DIR)/infer.make

infer-out/report.json: $(CLANG_DEPS) $(SOURCES) $(MAKEFILE_LIST)
	$(QUIET)$(REMOVE_DIR) buck-out && \
	$(call silent_on_success,Testing analysis with Objective-C getters and setters,\
	$(INFER_BIN) $(INFER_OPTIONS) --results-dir $(CURDIR)/infer-out -- clang -c  $(SOURCES))
