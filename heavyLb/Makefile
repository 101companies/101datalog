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
	echo "Depth:" >> log
	make -s depth >> log
	make -s precedence
	echo "Mentoring:" >> log
	make -s mentoring >> log
	diff baseline log

create:
	${bb} -create -overwrite
	${bb} -addBlock -file schema.logic

populate:
	${bb} -execute -file instance.logic

total:
	${bb} -query -file total.logic

cut:
	${bb} -execute -file cut.logic

depth:
	${bb} -query -file depth.logic -print _depthOfCompany

precedence:
	${bb} -addBlock -file precedence.logic

mentoring:
	${bb} -query '_(tee,tor) <- menteeOf(tee,tor).'

clean:
	rm -f log
	rm -rf workspace

