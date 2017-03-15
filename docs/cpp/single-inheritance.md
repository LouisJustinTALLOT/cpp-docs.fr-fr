---
title: "H&#233;ritage simple | Microsoft Docs"
ms.custom: ""
ms.date: "11/04/2016"
ms.reviewer: ""
ms.suite: ""
ms.technology: 
  - "devlang-cpp"
ms.tgt_pltfrm: ""
ms.topic: "language-reference"
f1_keywords: 
  - "single inheritance_cpp"
  - "single inheritance"
dev_langs: 
  - "C++"
helpviewer_keywords: 
  - "classes de base, indirectes"
  - "classes dérivées, classe de base unique"
  - "héritage, unique"
  - "opérateurs (C++), résolution de portée"
  - "opérateur de résolution de portée"
  - "portée, opérateur de résolution de portée"
  - "héritage simple"
ms.assetid: 1cb946ed-8b1b-4cf1-bde0-d9cecbfdc622
caps.latest.revision: 13
author: "mikeblome"
ms.author: "mblome"
manager: "ghogen"
caps.handback.revision: 13
---
# H&#233;ritage simple
[!INCLUDE[vs2017banner](../assembler/inline/includes/vs2017banner.md)]

Dans « l'héritage unique », une forme courante d'héritage, les classes possèdent une seule classe de base.  Considérons la relation illustrée à la figure ci\-dessous.  
  
 ![Graphique d'héritage unique simple](../cpp/media/vc38xj1.png "vc38XJ1")  
Graphique simple illustrant un héritage unique  
  
 Notez la progression d'un niveau général à un niveau spécifique dans la figure.  Un autre attribut courant figurant dans la conception de la plupart des hiérarchies de classes est que la classe dérivée possède une « sorte » de relation avec la classe de base.  Dans la figure ci\-dessus, un objet `Book` est une sorte d'objet `PrintedDocument` et un objet `PaperbackBook` est une sorte d'objet `book`.  
  
 Autre élément à retenir dans la figure : `Book` est à la fois une classe dérivée \(de `PrintedDocument`\) et une classe de base \(`PaperbackBook` est dérivé de `Book`\).  Le squelette de la déclaration d'une telle hiérarchie de classes est illustré dans l'exemple suivant :  
  
```  
// deriv_SingleInheritance.cpp  
// compile with: /LD  
class PrintedDocument {};  
  
// Book is derived from PrintedDocument.  
class Book : public PrintedDocument {};  
  
// PaperbackBook is derived from Book.  
class PaperbackBook : public Book {};  
```  
  
 `PrintedDocument` est considéré comme une classe « de base directe » pour `Book` ; c'est une classe « de base indirecte » pour `PaperbackBook`.  La différence tient au fait qu'une classe de base directe figure dans la liste de base d'une déclaration de classe, alors qu'une classe de base indirecte n'y figure pas.  
  
 La classe de base dont chaque classe est dérivée est déclarée avant la déclaration de la classe dérivée.  Il ne suffit pas de fournir une déclaration de référence avant pour une classe de base ; il faut fournir une déclaration complète.  
  
 Dans l'exemple précédent, le spécificateur d'accès **public** est utilisé.  La signification d'un héritage public, protégé et privé est décrite dans [Contrôle d'accès aux membres](../cpp/member-access-control-cpp.md).  
  
 Une classe peut servir de classe de base pour de nombreuses classes spécifiques, comme illustré à la figure suivante.  
  
 ![Graphique acyclique dirigé](../cpp/media/vc38xj2.png "vc38XJ2")  
Exemple de graphique acyclique dirigé  
  
 Dans le diagramme ci\-dessus, appelé « graphique acyclique dirigé », certaines classes sont des classes de base pour plusieurs classes dérivées.  Toutefois, l'inverse n'est pas vrai : il existe une seule classe de base directe pour chaque classe dérivée.  Le graphique de la figure représente une structure « d'héritage unique ».  
  
> [!NOTE]
>  Les graphiques acycliques dirigés ne sont pas propres à l'héritage unique.  Ils sont également utilisés pour représenter des cas d'héritage multiple.  Ce sujet est couvert dans l'article [Héritage multiple](http://msdn.microsoft.com/fr-fr/3b74185e-2beb-4e29-8684-441e51d2a2ca).  
  
 Dans un héritage, la classe dérivée contient les membres de la classe de base, ainsi que tous les nouveaux membres que vous ajoutez.  Par conséquent, une classe dérivée peut faire référence à des membres de la classe de base \(à moins que ces membres soient redéfinis dans la classe dérivée\).  L'opérateur de résolution de portée \(`::`\) peut être utilisé pour faire référence à des membres de classes de base directes ou indirectes, lorsque ces membres ont été redéfinis dans la classe dérivée.  Considérez cet exemple :  
  
```  
// deriv_SingleInheritance2.cpp  
// compile with: /EHsc /c  
#include <iostream>  
using namespace std;  
class Document {  
public:  
   char *Name;   // Document name.  
   void PrintNameOf();   // Print name.  
};  
  
// Implementation of PrintNameOf function from class Document.  
void Document::PrintNameOf() {  
   cout << Name << endl;  
}  
  
class Book : public Document {  
public:  
   Book( char *name, long pagecount );  
private:  
   long  PageCount;  
};  
  
// Constructor from class Book.  
Book::Book( char *name, long pagecount ) {  
   Name = new char[ strlen( name ) + 1 ];  
   strcpy_s( Name, strlen(Name), name );  
   PageCount = pagecount;  
};  
```  
  
 Notez que le constructeur de `Book`, \(`Book::Book`\), a accès aux données membres, `Name`.  Dans un programme, un objet de type `Book` peut être créé et utilisé comme suit :  
  
```  
//  Create a new object of type Book. This invokes the  
//   constructor Book::Book.  
Book LibraryBook( "Programming Windows, 2nd Ed", 944 );  
  
...  
  
//  Use PrintNameOf function inherited from class Document.  
LibraryBook.PrintNameOf();  
```  
  
 Comme le montre l'exemple précédent, le membre de classe et les données et fonctions héritées sont utilisés de façon identique.  Si l'implémentation de la classe `Book` demande une réimplémentation de la fonction `PrintNameOf`, la fonction qui appartient à la classe `Document` peut être appelée uniquement à l'aide de l'opérateur de résolution de portée \(`::`\) :  
  
```  
// deriv_SingleInheritance3.cpp  
// compile with: /EHsc /LD  
#include <iostream>  
using namespace std;  
  
class Document {  
public:  
   char *Name;          // Document name.  
   void  PrintNameOf() {}  // Print name.  
};  
  
class Book : public Document {  
   Book( char *name, long pagecount );  
   void PrintNameOf();  
   long  PageCount;  
};  
  
void Book::PrintNameOf() {  
   cout << "Name of book: ";  
   Document::PrintNameOf();  
}  
```  
  
 Les pointeurs et les références des classes dérivées peuvent être convertis implicitement en pointeurs et références de leurs classes de base, s'il existe une classe de base accessible et non équivoque.  Le code suivant illustre ce concept à l'aide de pointeurs \(le même principe s'applique aux références\) :  
  
```  
// deriv_SingleInheritance4.cpp  
// compile with: /W3  
struct Document {  
   char *Name;  
   void PrintNameOf() {}  
};  
  
class PaperbackBook : public Document {};  
  
int main() {  
   Document * DocLib[10];   // Library of ten documents.  
   for (int i = 0 ; i < 10 ; i++)  
      DocLib[i] = new Document;  
}  
```  
  
 Dans l'exemple précédent, des types différents sont créés.  Toutefois, comme ces types sont tous dérivés de la classe `Document`, il existe une conversion implicite vers `Document *`.  Par conséquent, `DocLib` est une « liste hétérogène » \(une liste dans laquelle tous les objets ne sont pas du même type\) contenant différents types d'objets.  
  
 Comme la classe `Document` possède une fonction `PrintNameOf`, elle peut imprimer le nom de chaque ouvrage de la bibliothèque, mais elle peut omettre certaines informations spécifiques au type de document \(nombre de pages pour `Book`, nombre d'octets pour `HelpFile`, etc.\).  
  
> [!NOTE]
>  Obliger la classe de base à implémenter une fonction telle que `PrintNameOf` est rarement le meilleur choix de conception.  Les [fonctions virtuelles](../cpp/virtual-functions.md) offrent d'autres alternatives de conception.  
  
## Voir aussi  
 [Vue d'ensemble des classes dérivées](../misc/overview-of-derived-classes.md)   
 [\(NOTINBUILD\) Multiple Inheritance](http://msdn.microsoft.com/fr-fr/3b74185e-2beb-4e29-8684-441e51d2a2ca)