---
title: BioJava:CookbookFrench:PDB:Read
---

Comment faire pour lire un fichier de type PDB?
-----------------------------------------------

La [*Protein Data Bank*](http://www.pdb.org) est la principale source de
données struturales disponible sur l'Internet. Contrairement aux
fichiers de type GenBank ou EMBL qui contiennent des donnés de séquence,
les fichiers PDB contiennent plutôt des données de position d'atomes au
sein d'une structure 3D. À partir de la version 1.4, BioJava est capable
de lire ces fichiers &agrve; l'aide des classes du package
org.biojava.bio.structure.io. Le code ci-dessous, introduit dans la
portion appropriée de votre programme (;-)), vous montre la marche à
suivre.

<java>

`// PDBFileREader peut egalement lire les archives`  
`// de type zip en entree`  
`String filename =  "parcours/vers/fichier.entree" ;`  
  
`PDBFileReader pdbreader = new PDBFileReader();`  
  
`try{`  
`    Structure struc = pdbreader.getStructure(filename);`  
`    System.out.println(struc);`  
`} catch (Exception e) {`  
`    e.printStackTrace();`  
`}`

</java>