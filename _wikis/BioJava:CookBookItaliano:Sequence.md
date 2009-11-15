---
title: BioJava:CookBookItaliano:Sequence
---

Come posso creare un oggetto Stringa a partire da una Sequenza e viceversa creare un oggetto Sequenza a partire da una Stringa?
-------------------------------------------------------------------------------------------------------------------------------

Molte volte ci imbattiamo in sequenze rappresentate da una Stringa di
caratteri come ad esempio "atgccgtggcatcgaggcatatagc". E' un metodo
conveniente per visualizzare e rappresentare in maniera sintetica un più
complesso polimero biologico. Biojava utilizza SymbolLists e Sequences
per rappresentare i polimeri biologici come Oggetti. Le Sequences
estendono le SymbolLists fornendo ulteriori metodi per memorizzare il
nome della sequenza e ogni tipo di caratteristica che potrebbe avere,
comunque basta pensare una Sequence come fosse una SymbolList.

Sia che si usi una Sequence che una SymbolList il polimero non verrà mai
memorizzato come una Stringa. Biojava differenza i residui di diversi
polimeri utilizzando oggetti di tipo Simobolo come provenienti da
Alfabeti diversi. In questa maniera è semplice dire se stiamo usando una
sequenza di DNA, di RNA o di qualcos'altro, inoltre è anche possibile
distinguere se un residuo 'A' appartiene a un DNA o ad un RNA. I
dettagli a riguardo di Symbols, SymbolLists e Alphabets sono trattati
qui. Questa è una parte cruciale perchè è la necessita di fornire al
programmatore un strada per effettuare una conversione fra un oggetto
Biojava a una Stringa semplice da leggere e da utilizzare, e viceversa.
Per fare questo Biojava usa dei Tokenizers che leggono una stringa di
testo e la interpretano per poi ottenere un oggetto BioJava Sequence o
SymbolList. Nel caso

`In the case of DNA, RNA and Protein you can do this with a single method call. The call is made to a static method from either DNATools, RNATools or ProteinTools.`

### String to SymbolList

<java> import org.biojava.bio.seq.\*; import org.biojava.bio.symbol.\*;

public class StringToSymbolList {

` public static void main(String[] args) {`  
`  `  
`   try {`  
`     //create a DNA SymbolList from a String`  
`     SymbolList dna = DNATools.createDNA("atcggtcggctta");`

`     //create a RNA SymbolList from a String`  
`     SymbolList rna = RNATools.createRNA("auugccuacauaggc");`

`     //create a Protein SymbolList from a String`  
`     SymbolList aa = ProteinTools.createProtein("AGFAVENDSA");`  
`   }`  
`   catch (IllegalSymbolException ex) {`  
`     //this will happen if you use a character in one of your strings that is`  
`     //not an accepted IUB Character for that Symbol.`  
`     ex.printStackTrace();`  
`   }`  
`  `  
` }`

} </java>

### String to Sequence

<java> import org.biojava.bio.seq.\*; import org.biojava.bio.symbol.\*;

public class StringToSequence {

` public static void main(String[] args) {`

`   try {`  
`     //create a DNA sequence with the name dna_1`  
`     Sequence dna = DNATools.createDNASequence("atgctg", "dna_1");`

`     //create an RNA sequence with the name rna_1`  
`     Sequence rna = RNATools.createRNASequence("augcug", "rna_1");`

`     //create a Protein sequence with the name prot_1`  
`     Sequence prot = ProteinTools.createProteinSequence("AFHS", "prot_1");`  
`   }`  
`   catch (IllegalSymbolException ex) {`  
`     //an exception is thrown if you use a non IUB symbol`  
`     ex.printStackTrace();`  
`   }`  
` }`

} </java>

### SymbolList to String

You can call the seqString() method on either a SymbolList or a Sequence
to get it's Stringified version.

<java> import org.biojava.bio.symbol.\*;

public class SymbolListToString {

` public static void main(String[] args) {`  
`   SymbolList sl = null;`  
`   //code here to instantiate sl`  
`  `  
`   //convert sl into a String`  
`   String s = sl.seqString();`  
` }`

} </java>