.PHONY: all
all : lib this run

.PHONY: lib
lib:
	$(MAKE) -C ../../.. lib
	$(MAKE) -C ../.. lib

.PHONY: this
this:
	if [ ! -d target/classes ] ; then mkdir -p target/classes ; fi
	javac -cp "../../../kiss.jar:../../kiss-pi.jar:/opt/pi4j/lib/*" -d "target/classes" -s "src/main/java" $$(find "src/main/java" -regex '[^._].*\.java$$')

.PHONY: run
run:
	java -cp "../../../kiss.jar:target/classes:../../kiss-pi.jar:/opt/pi4j/lib/*" kiss.util.Run

.PHONY: test
test: 
	java -cp "../../../kiss.jar:target/classes:../../kiss-pi.jar:/opt/pi4j/lib/*" kiss.util.Run --norun

.PHONY: clean
clean:
	/bin/rm -rf target/*
	/bin/rm -rf $$(find . -name '*~' -o -name '._*' -o -name '#*')
