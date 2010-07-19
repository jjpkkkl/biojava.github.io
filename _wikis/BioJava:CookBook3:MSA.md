---
title: BioJava:CookBook3:MSA
---

How to create a Multiple Sequence Alignment in BioJava
======================================================

<java>

public class TestMe {

`   public static void main(String[] args){`  
`       `  
`       String[] ids = new String[] {"Q21691", "Q21495", "O48771"};`  
`       `  
`       TestMe me = new TestMe();`  
`       try {`  
`           me.align(ids);`  
`       } catch (Exception e){`  
`           e.printStackTrace();`  
`       }`  
`   }`

`   private void align(String[] ids) throws Exception{`  
`       `  
`       `  
`       List`<ProteinSequence>` lst = new ArrayList< ProteinSequence>();`  
`       for (String id : ids){`  
`       `  
`           ProteinSequence seq = getSequenceForId(id);`  
`               `  
`           `  
`           System.out.println("id :" + id + " " + seq);`  
`           lst.add( seq);`  
`           System.out.println(seq.getOriginalHeader());`  
`       }`  
`               // just for the sake of testing, not required...`  
`       SubstitutionMatrix`<AminoAcidCompound>` matrix = new SimpleSubstitutionMatrix`<AminoAcidCompound>`();`  
`       List alig = Alignments.getAllPairsAlignments(lst, PairwiseAligner.GLOBAL, new SimpleGapPenalty(), matrix);`  
`       System.out.println(alig);`  
`       `  
`       Profile`<ProteinSequence,AminoAcidCompound>` profile = Alignments.getMultipleSequenceAlignment(lst, MSAEmulation.CLUSTALW);`  
`       System.out.println("Clustalw:" );`  
`       System.out.println(profile);`  
`       `  
`       `  
`       `  
`   }`  
`   public ProteinSequence getSequenceForId(String uniProtId) throws Exception{`  
`       String template = "`[`http://www.uniprot.org/uniprot/%s.fasta`](http://www.uniprot.org/uniprot/%s.fasta)`";`  
`       `  
`           URL uniprotFasta = new URL(String.format(template, uniProtId));`  
`           `  
`           LinkedHashMap`<String, ProteinSequence>` map = `  
`               FastaReaderHelper.readFastaProteinSequence(uniprotFasta.openStream());`  
`           `  
`           return map.get(uniProtId);`  
`           `  
`   }`  
`   `

}

</java>