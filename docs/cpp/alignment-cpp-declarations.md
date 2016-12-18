---
title: "Alignement (d&#233;clarations&#160;C++) | Microsoft Docs"
ms.custom: ""
ms.date: "12/05/2016"
ms.prod: "visual-studio-dev14"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
dev_langs: 
  - "C++"
ms.assetid: a986d510-ccb8-41f8-b905-433df9183485
caps.latest.revision: 4
caps.handback.revision: 4
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
---
# Alignement (d&#233;clarations&#160;C++)
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Une des fonctionnalités de bas niveau de C\+\+ est la possibilité de spécifier avec précision l'alignement des objets en mémoire afin d'exploiter au mieux les capacités d'une architecture matérielle spécifique.  Par défaut, le compilateur aligne les membres de classe et de structure par rapport à leur taille : les objets bool et char sont alignés sur des limites d'un octet, les objets short sur deux octets, les objets int sur quatre octets, et les objets long, double et long double sur huit octets.  Dans la plupart des scénarios, vous n'avez pas à vous préoccuper de l'alignement, car l'alignement par défaut est déjà optimal.  Dans certains cas toutefois, vous pouvez améliorer nettement les performances ou consommer beaucoup moins de mémoire en spécifiant un alignement personnalisé pour vos structures de données.  Avant Visual Studio 2015, vous pouviez utiliser les mots clés Microsoft spécifiques \_\_alignof et declspec\(alignas\) pour spécifier un alignement supérieur à la valeur par défaut.  Depuis Visual Studio 2015, vous devez utiliser les mots clés standard C\+\+11 [alignof et alignas](../cpp/alignof-and-alignas-cpp.md) pour garantir une portabilité maximale du code.  Les nouveaux mots clés se comportant intrinsèquement de la même façon que les extensions Microsoft, la documentation de ces extensions s'applique également aux nouveaux mots clés.  Pour plus d'informations, voir [\_\_alignof, opérateur](../cpp/alignof-operator.md) et [align](../cpp/align-cpp.md).  La norme C\+\+ ne spécifie pas de comportement de compression pour l'alignement sur des limites inférieures à celles du compilateur par défaut sur la plateforme cible. Dans ce cas, vous devez donc encore utiliser le \#pragma [pack](../preprocessor/pack.md) de Microsoft.  
  
 La bibliothèque standard C\+\+ fournit la [aligned\_storage, classe](../standard-library/aligned-storage-class.md) pour allouer de la mémoire aux structures de données présentant des alignements personnalisés. Elle fournit aussi la [aligned\_union, classe](../standard-library/aligned-union-class.md) qui permet de spécifier l'alignement pour les unions contenant des constructeurs ou des destructeurs non triviaux.  
  
## Présentation de l'alignement  
 L'alignement est une propriété d'une adresse mémoire, exprimée sous la forme de l'adresse numérique modulo une puissance de 2.  Par exemple, l'adresse 0x0001103F modulo 4 est 3. Cette adresse est considérée comme étant alignée sur 4n\+3, où 4 indique la puissance de 2 choisie.  L'alignement d'une adresse dépend de la puissance de 2 choisie.  La même adresse modulo 8 est 7.  Une adresse est considérée comme étant alignée sur X si son alignement est Xn\+0.  
  
 Les processeurs exécutent des instructions qui opèrent sur des données stockées en mémoire, ces données étant identifiées par leur adresse en mémoire.  Chaque donnée a une adresse distincte, mais également une taille spécifique.  Une donnée est naturellement considérée comme alignée si son adresse est alignée sur sa taille. Sinon, elle est considérée comme non alignée.  Par exemple, une donnée à virgule flottante de 8 octets est naturellement alignée si l'adresse utilisée pour l'identifier est alignée sur 8.  
  
 Les compilateurs matériels gèrent l'alignement des données en essayant d'allouer les données d'une manière qui empêche tout mauvais alignement.  
  
 Pour les types de données simples, le compilateur assigne des adresses qui sont des multiples de la taille en octets du type de données.  Par conséquent, le compilateur assigne des adresses aux variables de type long qui sont des multiples de quatre, en définissant les deux derniers octets des adresses à zéro.  
  
 De plus, le compilateur remplit les structures de façon à aligner naturellement chaque élément des structures.  Examinons la structure struct x\_ dans l'exemple de code suivant :  
  
```  
struct x_  
{  
   char a;     // 1 byte  
   int b;      // 4 bytes  
   short c;    // 2 bytes  
   char d;     // 1 byte  
} MyStruct;  
  
```  
  
 Le compilateur remplit cette structure pour appliquer naturellement l'alignement.  
  
 L'exemple de code suivant montre comment le compilateur place la structure remplie dans memory:Copy  
  
```  
// Shows the actual memory layout  
struct x_  
{  
   char a;            // 1 byte  
   char _pad0[3];     // padding to put 'b' on 4-byte boundary  
   int b;            // 4 bytes  
   short c;          // 2 bytes  
   char d;           // 1 byte  
   char _pad1[1];    // padding to make sizeof(x_) multiple of 4  
}  
  
```  
  
1.  Les deux déclarations retournent une valeur sizeof\(struct x\_\) de 12 octets.  
  
2.  La deuxième déclaration inclut deux éléments de remplissage :  
  
3.  char \_pad0\[3\] pour aligner le membre int b sur une limite de 4 octets  
  
4.  char \_pad1\[1\] pour aligner les éléments tableau de la structure struct \_x bar\[3\];  
  
5.  Le remplissage aligne les éléments de bar\[3\] pour permettre un accès naturel.  
  
 L'exemple de code suivant illustre la disposition de tableau bar\[3\] :  
  
```  
adr offset   element  
------   -------  
0x0000   char a;         // bar[0]  
0x0001   char pad0[3];  
0x0004   int b;  
0x0008   short c;  
0x000a   char d;  
0x000b   char _pad1[1];  
  
0x000c   char a;         // bar[1]  
0x000d   char _pad0[3];  
0x0010   int b;  
0x0014   short c;  
0x0016   char d;  
0x0017   char _pad1[1];  
  
0x0018   char a;         // bar[2]  
0x0019   char _pad0[3];  
0x001c   int b;  
0x0020   short c;  
0x0022   char d;  
0x0023   char _pad1[1];  
  
```  
  
## Voir aussi  
 [Alignement des structures de données](http://en.wikipedia.org/wiki/Data_structure_alignment)