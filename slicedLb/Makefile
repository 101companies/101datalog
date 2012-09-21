bb = bloxbatch -db workspace

test:
	rm -f log
	touch log
	make create-and-populate
	echo "Initial total:" >> log
	make -s total >> log
	make -s cut
	echo "Total after cut:" >> log
	make -s total >> log
	diff baseline log


create-and-populate:
	${bb} -create -overwrite
	bloxbatch -script data/companies.lb
	bloxbatch -script data/departments.lb
	bloxbatch -script data/employees.lb
	bloxbatch -script data/managers.lb

total:
	${bb} -query -file total.logic

cut:
	${bb} -execute -file cut.logic

clean:
	rm -f log
	rm -rf workspace

