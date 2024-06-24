[[hardware/_intro/chain/design flow|design flow]]

[[hardware/VLSI and IP/Intellectual Properties|IP]] soft firm hard

third part [[hardware/VLSI and IP/Intellectual Properties|IP]] and [[hardware/VLSI and IP/RTL - register transfer level|RTL]] designing: 
**soft [[hardware/VLSI and IP/Intellectual Properties|IP]] Trojans**: written directly in 3rd party [[hardware/VLSI and IP/RTL - register transfer level|RTL]]. Undocumented functionality, hard to spot in large projects (code reviews are tedious and expensive). Also with test and simulation is hard to detect it


[[hardware/VLSI and IP/logic synthesis|synthesis tool]], which are often proprietary and expensive, are potential vectors for Trojan insertion. Companies usually don't have access to the source code of these tools
**firm 3rd Party IP Trojans**: insert into [[hardware/VLSI and IP/logic synthesis|synthesized]] [[hardware/VLSI and IP/netlist|netlists]], or in the source-code RTL or manually in the netlist. This can also be obfuscated

[[hardware/VLSI and IP/placement|placement]] and [[hardware/VLSI and IP/routing|routing]] are another area where trojan can be inserted. Manual intervention is rare, making them a simple target for injecting malicious code
**Malicious CAD Tool Trojans**: like synthesizer but in place e route


[[hardware/_intro/chain/fabrication|fabrication]] is another stage where trojan can be introduced, either during the manufacturing process or afterwards in the packaging stage. Often, fabrication and packaging are distributed across multiple locations, adding more vulnerability
**hard IP & Foundry Trojans**: [[hardware/_intro/chain/fabrication|foundry]] may edit circuit design 




