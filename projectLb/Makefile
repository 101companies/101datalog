bb = bloxbatch -db workspace

test:
	rm -f log
	touch log
	make -s create
	make -s populate
	echo "Initial total:" >> log
	make -s total >> log
	make -s cut
	echo "Total after cut:" >> log
	make -s total >> log
	diff baseline log

create:
	${bb} -create -overwrite
	make -s compile
	make -s install

compile:
	bloxcompiler -compileProject projectLb.project

install:
	${bb} -installProject -dir .

populate:
	bloxbatch -script instance.lb

total:
	bloxbatch -script total.lb

cut:
	${bb} -execute -file cut.logic

clean:
	rm -f log
	rm -rf workspace
	find . -name "LB_SUMMARY.lbp" -exec rm {} \;
	find . -name "*.lbb" -exec rm {} \;

