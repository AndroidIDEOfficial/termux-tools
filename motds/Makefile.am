# Copyright (C) 2022 Termux

# This file is part of termux-tools.

# termux-tools is free software: you can redistribute it and/or modify
# it under the terms of the GNU General Public License as published by
# the Free Software Foundation, either version 3 of the License, or
# (at your option) any later version.

# termux-tools is distributed in the hope that it will be useful, but
# WITHOUT ANY WARRANTY; without even the implied warranty of
# MERCHANTABILITY or FITNESS FOR A PARTICULAR PURPOSE.  See the GNU
# General Public License for more details.

# You should have received a copy of the GNU General Public License
# along with termux-tools.  If not, see
# <https://www.gnu.org/licenses/>.


# We have two variants of our motd message loaded by login script:
#   1. motd.sh: A dynamic motd that is executed with bash and echos a
#      motd message with escape sequences, optionally with a terminal logo.
#   2. motd: A static motd that is just read as is with cat and displayed.

# The motd-playstore is an additional motd that will only be displayed
# if the termux-app version is very old (like the version found on playstore)
sysconf_DATA = motd.sh motd

CLEANFILES = motd.sh motd

do_subst = sed -e "s%[@]TERMUX_PREFIX[@]%$(termux_prefix)%g"

define process-rule
$1: $1.in Makefile
	@echo "Creating $1"
	@$$(do_subst) < $(srcdir)/$1.in > $1
endef

$(eval $(call process-rule,motd.sh))


motd:
	@echo "Creating motd file"

	@echo "Welcome to AndroidIDE Terminal!" > motd
	@echo "" >> motd
	@echo "Blogs:      https://androidide.com/blogs/" >> motd
	@echo "Docs:       https://androidide.com/docs/" >> motd
	@echo "Community:  https://t.me/androidide_discussions" >> motd
	@echo "Updates:    https://t.me/AndroidIDEOfficial" >> motd
	@echo "Donate:     https://androidide.com/donate/" >> motd

        @echo "" >> motd
        @echo "Setup AndroidIDE:" >> motd
        @echo "" >> motd
        @echo " - Setup IDE: idesetup -c" >> motd

	@echo "" >> motd
	@echo "Working with packages:" >> motd
	@echo "" >> motd
	@echo " - Search:  pkg search <query>" >> motd
	@echo " - Install: pkg install <package>" >> motd
	@echo " - Upgrade: pkg upgrade" >> motd

	@echo "" >> motd
	@echo "Report issues at https://github.com/AndroidIDEOfficial/AndroidIDE/issues" >> motd
