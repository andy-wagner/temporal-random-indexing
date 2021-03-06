Temporal Random Indexing for the UK Web Archive
==================================================

General info
---------------

This software provides a framework for the Temporal Random Indexing (TRI) technique. TRI is able to build WordSpaces taking into account temporal information. A WordSpace is a geometrical space in which words are represented as mathematical points. Similar words are represented close in the WordSpace. TRI can build different WordSpaces for several time periods allowing the analysis of how words change their meaning over time.

The WordSpaces are built by exploiting the output of the project https://github.com/alan-turing-institute/UKWebArchive_semantic_change

Details about the algorithm are published in the following paper:

@inproceedings{clic2014a,<br>
	title            = "Analysing Word Meaning over Time by Exploiting Temporal Random Indexing",<br>
	year             = "2014",<br>
	author           = "Pierpaolo Basile and Annalina Caputo and Giovanni Semeraro",<br>
	booktitle        = "First Italian Conference on Computational Linguistics CLiC-it 2014",<br>
	editor           = "Roberto Basili and Alessandro Lenci and Bernardo Magnini",<br>
	publisher        = "Pisa University Press",<br>
	url              = "http://clic.humnet.unipi.it/proceedings/Proceedings-CLICit-2014.pdf"}<br>

Please, cite the paper if you adopt our tool.

The tool was also used and further developed in the following publication:

Basile, P., and McGillivray, B. (2018). Exploiting the Web for Semantic Change Detection. Discovery Science 2018 (Vol. 5, pp. 194–208). Springer International Publishing. https://doi.org/10.1007/978-3-030-01771-2_13

and was the starting point for  this project https://github.com/adtsakal/Semantic_Change described in the following publication:

Tsakalidis, A., Bazzi, M., Cucuringu, M., Basile, P., Mcgillivray, B., Alan, T., & Kingdom, U. (2019). Mining the UK Web Archive for Semantic Change Detection. In Proceedings of International Conference Recent Advances in Natural Language Processing. Retrieved from https://ora.ox.ac.uk/objects/uuid:19258068-98ab-444f-a8f0-e3389be618f2


Setup
--------

1.  Install Java JDK 1.7, Maven, Git.
2.  Clone the project using Git.
3.  Compile the project using the command: *mvn package*.
4.  Rename the file config.ex.properties in config.properties and set the parameters in the config file.
5.  Execute the bash script run.sh followed by the class name and arguments (see Command Line Guideline for more details).

Usage
--------

The first step is to prepare the corpus by using the tool https://github.com/alan-turing-institute/UKWebArchive_semantic_change 

In particular:

1. Covert ARC/WARC files in WET
2. Tokenize WET files

The next steps are (see Command Line Guideline for more details):

1. Build the dictionary
2. Build co-occurrence matrices
3. Build WordSpaces using Temporal Random Indexing

Command Line Guideline
-------------------------

**Build the dictionary**

Run the class *di.uniba.it.tri.occ.ati.dict.BuildDict*. This class builds the dictionary using the parameters in the file *config.properties*.

**Build co-occurrence matrices**

Run the class *di.uniba.it.tri.occ.ati.occ.BuildOccurrenceATI*. This class builds the co-occurrence matrices using the parameters in the file *config.properties*.

**Build WordSpaces using Temporal Random Indexing**

Run the class **di.uniba.it.tri.space.SpaceBuilderDict**. 

usage: Build WordSpace using Temporal Random Indexing [-c <arg>] [-d <arg>] [-dict <arg>] [-idf <arg>] [-minocc <arg>] [-o <arg>] [-rv <arg>] [-s <arg>] [-self <arg>] [-t <arg>] <br>
 -c <arg>        The directory containing the co-occurrence matrices <br>
 -d <arg>        The vector dimension (optional, default is 300) <br>
 -dict <arg>     The dictionary file <br>
 -idf <arg>      Enable IDF (optinal, default is false) <br>
 -minocc <arg>   This will discard words that appear less than <int> times (optional, default is 5) <br>
 -o <arg>        Output directory where WordSpaces will be stored <br>
 -rv <arg>       Random vectors files (optional) <br>
 -s <arg>        The number of seeds (optional, default is 10) <br>
 -self <arg>     Inizialize using random vector (optinal, default is false) <br>
 -t <arg>        Threshold for downsampling frequent words (optinal, default is 0.001) <br>

Contacts
-----------
Pierpaolo Basile, pierpaolo.basile@gmail.com.
