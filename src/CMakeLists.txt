# MaNGOS is a full featured server for World of Warcraft, supporting
# the following clients: 1.12.x, 2.4.3, 3.2.5a, 4.2.3 and 5.4.8
#
# Copyright (C) 2005-2014  MaNGOS project <http://getmangos.eu>
#
# ***** BEGIN GPL LICENSE BLOCK *****
#
# This program is free software; you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation; either version 2 of the License, or
# (at your option) any later version.
#
# This program is distributed in the hope that it will be useful,
# but WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the
# GNU General Public License for more details.
#
# You should have received a copy of the GNU General Public License
# along with this program; if not, write to the Free Software
# Foundation, Inc., 59 Temple Place, Suite 330, Boston, MA  02111-1307  USA
#
# ***** END GPL LICENSE BLOCK *****
#
# World of Warcraft, and all World of Warcraft or Warcraft art, images,
# and lore are copyrighted by Blizzard Entertainment, Inc.

# Needs to link against mangos_worldd.lib
if(WIN32)
  link_directories(
    "${CMAKE_BINARY_DIR}/src/mangosd/${CMAKE_CFG_INTDIR}"
  )
  include_directories(
    "${CMAKE_SOURCE_DIR}/dep/include"
  )
endif()

#-----------------------------------------------------------------------------
# Build the mangos-zero framework library
add_subdirectory(framework)

#-----------------------------------------------------------------------------
# Build the mangos-zero shared library
add_subdirectory(shared)

#-----------------------------------------------------------------------------
# Build the mangos-zero game library
add_subdirectory(game)

#-----------------------------------------------------------------------------
# Build the mangos-zero realm authentication server
add_subdirectory(realmd)

#-----------------------------------------------------------------------------
# Build the mangos-zero world server
add_subdirectory(mangosd)

#-----------------------------------------------------------------------------
# If we want the tools for map/vmap/mmap extraction
if(BUILD_TOOLS)
    add_subdirectory(tools)
endif()

#-----------------------------------------------------------------------------
# Build the mangos-zero script library
add_subdirectory(scripts)
