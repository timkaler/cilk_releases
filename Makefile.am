# Copyright (C) 2011 , Intel Corporation
# All rights reserved.
# 
# Redistribution and use in source and binary forms, with or without
# modification, are permitted provided that the following conditions
# are met:
# 
#   * Redistributions of source code must retain the above copyright
#     notice, this list of conditions and the following disclaimer.
#   * Redistributions in binary form must reproduce the above copyright
#     notice, this list of conditions and the following disclaimer in
#     the documentation and/or other materials provided with the
#     distribution.
#   * Neither the name of Intel Corporation nor the names of its
#     contributors may be used to endorse or promote products derived
#     from this software without specific prior written permission.
# 
# THIS SOFTWARE IS PROVIDED BY THE COPYRIGHT HOLDERS AND CONTRIBUTORS
# "AS IS" AND ANY EXPRESS OR IMPLIED WARRANTIES, INCLUDING, BUT NOT
# LIMITED TO, THE IMPLIED WARRANTIES OF MERCHANTABILITY AND FITNESS FOR
# A PARTICULAR PURPOSE ARE DISCLAIMED. IN NO EVENT SHALL THE COPYRIGHT
# HOLDER OR CONTRIBUTORS BE LIABLE FOR ANY DIRECT, INDIRECT,
# INCIDENTAL, SPECIAL, EXEMPLARY, OR CONSEQUENTIAL DAMAGES (INCLUDING,
# BUT NOT LIMITED TO, PROCUREMENT OF SUBSTITUTE GOODS OR SERVICES; LOSS
# OF USE, DATA, OR PROFITS; OR BUSINESS INTERRUPTION) HOWEVER CAUSED
# AND ON ANY THEORY OF LIABILITY, WHETHER IN CONTRACT, STRICT
# LIABILITY, OR TORT (INCLUDING NEGLIGENCE OR OTHERWISE) ARISING IN ANY
# WAY OUT OF THE USE OF THIS SOFTWARE, EVEN IF ADVISED OF THE
# POSSIBILITY OF SUCH DAMAGE.

AUTOMAKE_OPTIONS = foreign
ACLOCAL_AMFLAGS = -I m4

# Compiler and linker flags.
GENERAL_FLAGS = -I$(top_srcdir)/include
GENERAL_FLAGS += -fpic -O3
GENERAL_FLAGS += -DBUILD_USER=\"$(USER)\"
GENERAL_FLAGS += -DBUILD_HOST=\"`hostname`\"
AM_CFLAGS = $(GENERAL_FLAGS) -std=c99
AM_CPPFLAGS = $(GENERAL_FLAGS)
AM_LDFLAGS = -lpthread -ldl

# Target list.
lib_LTLIBRARIES = libcilkrts.la

libcilkrts_la_SOURCES = runtime/cilk-abi.c runtime/cilk_api.c           \
  runtime/cilk_malloc.c runtime/c_reducers.c                            \
  runtime/frame_malloc.c runtime/full_frame.c runtime/jmpbuf.c          \
  runtime/local_state.c runtime/metacall_impl.c runtime/os_mutex-unix.c \
  runtime/os-unix.c runtime/scheduler.c runtime/signal_node.c           \
  runtime/stacks.c runtime/stats.c runtime/symbol_test.c                \
  runtime/sysdep-unix.c runtime/worker_mutex.c runtime/bug.cpp          \
  runtime/cilk-abi-cilk-for.cpp runtime/except-gcc.cpp                  \
  runtime/global_state.cpp runtime/reducer_impl.cpp

# Load the $(REVISION) value.
include include/internal/rev.mk

libcilkrts_la_LDFLAGS  = -rpath '$(libdir)'
libcilkrts_la_LDFLAGS += -version-info 5:$(CILK_REVISION):0
libcilkrts_la_LDFLAGS += -lpthread -ldl

# C/C++ header files for Cilk.
cilkincludedir = $(includedir)/cilk
cilkinclude_HEADERS =              \
  include/cilk/cilk_api.h          \
  include/cilk/cilk_api_linux.h    \
  include/cilk/cilk.h              \
  include/cilk/cilk_stub.h         \
  include/cilk/cilk_undocumented.h \
  include/cilk/common.h            \
  include/cilk/holder.h            \
  include/cilk/hyperobject_base.h  \
  include/cilk/reducer_file.h      \
  include/cilk/reducer.h           \
  include/cilk/reducer_list.h      \
  include/cilk/reducer_max.h       \
  include/cilk/reducer_min.h       \
  include/cilk/reducer_opadd.h     \
  include/cilk/reducer_opand.h     \
  include/cilk/reducer_opor.h      \
  include/cilk/reducer_opxor.h     \
  include/cilk/reducer_ostream.h   \
  include/cilk/reducer_string.h