test:
	rm -f log
	touch log
	make -s compile
	make -s create
	make -s install
	make -s populate
	echo "Initial total:" >> log
	make -s total >> log
	make -s cut
	echo "Total after cut:" >> log
	make -s total >> log
	diff baseline log

compile:
	bloxcompiler -compileProject modularLb.project

create:
	lb create --overwrite workspace > /dev/null

install:
	lb addproject workspace .

populate:
	lb execblock workspace oneOone:Instance

total:
	lb execblock --print workspace oneOone:Total 

cut:
	lb execblock workspace oneOone:Cut 

clean:
	rm -f log
	-lb delete workspace > /dev/null 2> /dev/null
	find . -name "LB_SUMMARY.lbp" -exec rm {} \;
	find . -name "*.lbb" -exec rm {} \;

