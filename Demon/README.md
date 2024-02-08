# Demon

Two-dimensional cyclic cellular automaton. [Wikipedia](https://en.wikipedia.org/wiki/Cyclic_cellular_automaton)

Here is the ouput after 30 generations (one generation runs in about 10 minutes).

	3454321876565432345678767812
	4565432187654543334567678123
	5676543218765654333456781234
	6787654321876765434567812345
	7818765432187876545678123456
	8127654321878187656781234567
	1234543218781218767812345678
	8123432187812321878181234567
	7812321878123432181211123456
	6781218781234543212321112545
	5678187678121654323412111656
	8567876567818765434543211767
	1678187656787654345612188778
	2343218765676543456781877781

It's kind of hard to see the demons (spirals) without colors...  
You can change the random seed at line 1, word 24.

Lucien Baumann 2024

## demon.pti

An executable tape image with included (french) commented source code for the demon program.
This image is not bootable.
You should have previously initialized the system using a tape that contains the number track. 