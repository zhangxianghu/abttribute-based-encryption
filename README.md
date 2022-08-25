# abttribute-based-encryption

This project shows a simple example to use the basic functions of ABE, especially CP-ABE. 

### Example
	1. Choose a simple policy A OR (B AND C), where attributes: A= 123-456-789, B=General  hospital, C=Cardiologist 

	2. Key generation for three users: 
		a) Alice with attributes: 100-20-3456, General  hospital, Cardiologist, 
		b) Bob with attributes: 123-45-6789, ABC Pte Ltd, Programmer, 
		c) Mallory with attributes: 123-00-1234, ABC Pte Ltd, Programmer

	3. Encryption of a large file M of 1GB by data owner

	4. Decryption by Alice, Bob, Mallory using their keys

### CP-ABE toolkit
	We use the CP-ABE toolkit: CP-ABE package in Advanced Crypto Software Collection (ACSC) by John Bethencourt, Amit Sahai, Brent Waters. Download at http://acsc.cs.utexas.edu/cpabe/

	Another choice is Functional Encryption Library (libfenc) ABE library/extensions by Matthew Green, Ayo Akinyele, Michael Rushanan. Download at http://code.google.com/p/libfenc

### Instructions to use ACSC
	1. Download the necessary libraries to a target folder in Ubuntu 
		a) PBC Library: pbc-0.5.14 (https://crypto.stanford.edu/pbc/download.html)
		b) Libbswabe Libarary: libbswabe-0.9 (http://acsc.cs.utexas.edu/cpabe/)
		c) GMP Library: Gmp-6.1.2 (https://gmplib.org/)
		d) cpabe Toolkit: Cpabe-0.11 (http://acsc.cs.utexas.edu/cpabe/)

	2. Install necessary libraries through terminal (on Mac, install Homebrew and use brew instead of apt-get)
		a) sudo apt-get update
		b)sudo apt-get install flex
		c)sudo apt-get install bison
		d)sudo apt-get install libffi-dev
		e)sudo apt-get install libmount-dev
		f)sudo apt-get install libpcre3-dev
		g)sudo apt-get install libglib2.0-dev
		h)sudo apt-get install libssl-dev

	3. Compile, and install the three libraries gmp pbc libbswabe and cpabe toolkit though terminal under their folders
		a)	./configure
		b)	make
		c)	sudo make install

	   Notes:
		a) Unzip tar.gz file using tar -zxvf target-file.tar.gz
		b) To unzip tar.lz file, you may need to install lunzip first https://zoomadmin.com/HowToInstall/UbuntuPackage/lunzip 
			And then “lunzip target.tar.gz”, and then “tar xvf target.tar”
		c) ``./configure pbc -> make -> sudo make install``
		d) ./configure libbswabe -> make -> sudo make install
			If GLIB is not installed correctly, try: sudo apt-get install libgtk2.0-dev
		e) ./configure gmp -> make -> sudo make install
		f) ./configure cpabe -> make (had to edit by adding -lgmp to Makefile) -> sudo make install
			Note: before make, find the following and adding -lgmp
			"-lbswabe \"
			"-lcrypto -lcrypto \"
			"-lgmp"

	4. If everything is okay, set up master key and public key in your working folder using the following command: 
		cpabe-setup
	
	5. Generate private keys associated with a set of attributes for the users using the master key and public key:
		cpabe-keygen -o <output name> pub_key master_key \ 
 		<attributes>

 		E.g.: cpabe-keygen -o sara_priv_key pub_key master_key \
    			sysadmin it_department 'office = 1431'












