---
title: BioJava:CookbookFrench:PDB:AtomCalc
---

Comment faire des calculs sur des Atomes présent dans un fichier PDB?
---------------------------------------------------------------------

La classe Calc vous procure une série de méthodes permettant de faire
divers calculs sur des Atomes.

<java> public double getPhi(Group a, Group b)

`   throws StructureException`  
`   {`  
`       `  
`       if ( ! Calc.isConnected(a,b)){`  
`           throw new StructureException("can not calc Phi - AminoAcids are not connected!") ;`  
`       } `  
`       `  
`       Atom a_C  = a.getAtom("C");`  
`       Atom b_N  = b.getAtom("N");`  
`       Atom b_CA = b.getAtom("CA");`  
`       Atom b_C  = b.getAtom("C");`  
`       `  
`       double phi = Calc.torsionAngle(a_C,b_N,b_CA,b_C);`  
`       return phi ;`  
`   }`

</java>