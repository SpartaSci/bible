Numerous **challenges**:
handling **many designs**
Being **non-destructive** to the IC
Being **cost-effective**
Ability to Detect trojans of **different sizes** or complexities
Authenticating chips in as **small a time** frame as possible
Robust variations in manufacturing processes



**Destructive**: this involves taking a sample from each [[hardware/_intro/chain/fabrication|factory]] batch, opening the chip, and checking every part of the manufacturing process, including all masks and steps. *Time-consuming and costly*

**Non-destructive**:
- **invasive**: changing the state of the system to trigger the trojan
- **non-invasive**: 
	- **run-time**: the system continuously monitor the abnormal behavior during operation
	- **test-time**: 
		- standard **logic test**
		- [[hardware/attack taxonomy/side channel/_side channel|_side channel]]: power consumption and electromagnetic emissions 
