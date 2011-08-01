---
title: BioJava:CookBook3:ProteinDisorder
---

How can I predict disordered regions on the protein sequence?
-------------------------------------------------------------

BioJava provide a module *biojava3-protein-disorder* for prediction
disordered regions from protein sequence.

Biojava3-protein-disorder module for now contains one method for the
prediction of disordered regions from protein sequence. This method is
based on the Java implementation of
[RONN](http://www.strubi.ox.ac.uk/RONN) predictor.

This code has been originally developed for use with
[JABAWS](http://www.compbio.dundee.ac.uk/jabaws). We call this code
*JRONN*. *JRONN* is based on the C implementation of RONN algorithm and
uses the same model data, therefore gives the same predictions. Main
motivation behind JRONN development was providing an implementation of
RONN more suitable to use by the automated analysis pipelines and web
services.

Robert Esnouf has kindly allowed us to explore the RONN code and share
the results with the community.

Original version of RONN is described in Yang,Z.R., Thomson,R.,
McMeil,P. and Esnouf,R.M. (2005) RONN: the bio-basis function neural
network technique applied to the detection of natively disordered
regions in proteins Bioinformatics 21: 3369-3376

Example 1: Calculate the probability of disorder for every residue in the sequence
----------------------------------------------------------------------------------

<java> FastaSequence fsequence = new FastaSequence("name",
"LLRGRHLMNGTMIMRPWNFLNDHHFPKFFPHLIEQQAIWLADWWRKKHC" +

`               "RPLPTRAPTMDQWDHFALIQKHWTANLWFLTFPFNDKWGWIWFLKDWTPGSADQAQRACTWFFCHGHDTN");`

float[] rawProbabilityScores = Jronn.getDisorderScores(fsequence);
</java>

Example 2: Calculate the probability of disorder for every residue in the sequence for all proteins from the FASTA input file
-----------------------------------------------------------------------------------------------------------------------------

<java> final List<FastaSequence> sequences = SequenceUtil.readFasta(new
FileInputStream("src/test/resources/fasta.in"));
Map<FastaSequence, float[]> rawProbabilityScores =
Jronn.getDisorderScores(sequences); </java>

Example 3: Get the disordered regions of the protein for a single protein sequence
----------------------------------------------------------------------------------

<java> FastaSequence fsequence = new FastaSequence("Prot1",
"LLRGRHLMNGTMIMRPWNFLNDHHFPKFFPHLIEQQAIWLADWWRKKHC" +

`               "RPLPTRAPTMDQWDHFALIQKHWTANLWFLTFPFNDKWGWIWFLKDWTPGSADQAQRACTWFFCHGHDTN" +`  
`               "CQIIFEGRNAPERADPMWTGGLNKHIIARGHFFQSNKFHFLERKFCEMAEIERPNFTCRTLDCQKFPWDDP");`

Range[] ranges = Jronn.getDisorder(fsequence); </java>

Example 4: Calculate the disordered regions for the proteins from FASTA file
----------------------------------------------------------------------------

<java> final List<FastaSequence> sequences = SequenceUtil.readFasta(new
FileInputStream("src/test/resources/fasta.in"));
Map<FastaSequence, Range[]> ranges = Jronn.getDisorder(sequences);

</java>