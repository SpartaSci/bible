> **Autopsy** is an open-source digital forensics platform that is both **multi-platform** and **multi-user**

**Autopsy workflow**:
1. creating a case
2. import relevant data
	- files
	- hard disk images
	- virtual machine images
3. initiation of **keyword searches** and **hash analysis** 
	- in depth data analysis using content viewers
4. **report** (in HTML/XML) with the findings


Autopsy enables **interactive access to results** as they are discovered. This is achieved through features such as partial keyword search results, which are provided at regular intervals (e.g. every 5 minutes), and the ability to prioritize specific folders for analysis.


default modules: 
- recent activity extractor
- hash calculation
- file type identification
- embedded file extractor
- [[computer forensics/tools/exiftool|exif]] parser 
- keyword search and email parser



> [!important] **Timeline** is an important features





The NIST NSRL build Reference Data Set with digial signature of known software application

In Autopsy, the NSRL database is used to enhance the identification and analysis of files during investigations
comparing the hashes


