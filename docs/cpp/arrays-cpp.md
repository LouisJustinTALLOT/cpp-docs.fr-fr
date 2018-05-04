---
title: Tableaux (C++) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- declaring arrays [C++], about declaring arrays
- multidimensional arrays [C++]
- arrays [C++]
ms.assetid: 3f5986aa-485c-4ba4-9502-67e2ef924238
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 0fe8e5f53d05ac159fd577b260268f297b59d146
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
---
# <a name="arrays-c"></a>Tableaux (C++)
Un tableau est une collection d’objets similaires. Le cas le plus simple d'un tableau est celui d'un vecteur, qui peut être déclaré par la séquence suivante :  
  
```  
  
      decl-specifier identifier [ constant-expression ]  
decl-specifier identifier []  
decl-specifier identifer [][ constant-expression] . . .  
decl-specifier identifier [ constant-expression ]  
[ constant-expression ] . . .  
```  
  
 1. Spécificateur de déclaration :  
  
-   Spécificateur de classe de stockage facultatif.  
  
-   Facultatif **const** et/ou `volatile` spécificateurs.  
  
-   Nom de type des éléments du tableau.  
  
 2. Déclarateur :  
  
-   Identificateur.  
  
-   Une expression constante de type intégral placée entouré crochets, **[].** Si plusieurs dimensions sont déclarées à l’aide de crochets supplémentaires, l’expression constante peut être omise sur le premier jeu de crochets.  
  
-   Crochets supplémentaires facultatifs englobant des expressions constantes.  
  
 3. Initialiseur facultatif.  Consultez [initialiseurs](../cpp/initializers.md).  
  
 Le nombre d'éléments du tableau est fourni par l'expression constante. Le premier élément du tableau est l’élément 0, et le dernier élément est le (*n*-1) élément, où *n* est le nombre d’éléments du tableau peut contenir. Le *expression constante* doit être de type intégral et doit être supérieure à 0. Un tableau de taille zéro est autorisé uniquement lorsque le tableau est le dernier champ dans un `struct` ou **union** et que les extensions Microsoft (/Ze) sont activées.  
  
 L'exemple suivant montre comment définir un tableau au moment de l'exécution :  
  
```  
// arrays.cpp  
// compile with: /EHsc  
#include <iostream>  
  
int main() {  
   using namespace std;  
   int size = 3, i = 0;  
  
   int* myarr = new int[size];  
  
   for (i = 0 ; i < size ; i++)  
      myarr[i] = 10;  
  
   for (i = 0 ; i < size ; i++)  
      printf_s("myarr[%d] = %d\n", i, myarr[i]);  
  
   delete [] myarr;  
}  
```  
  
 Les tableaux sont des types dérivés et peuvent donc être construits à partir de tout autre type dérivé ou principal, excepté les fonctions, les références et `void`.  
  
 Les tableaux construits à partir d'autres tableaux sont des tableaux multidimensionnels. Ces tableaux multidimensionnels sont spécifiés en plaçant dans l'ordre plusieurs expressions de constantes entre accolades. Par exemple, observez cette déclaration :  
  
```  
int i2[5][7];  
```  
  
 Elle spécifie un tableau de type `int`, organisé conceptuellement selon une matrice à deux dimensions de cinq lignes et sept colonnes, comme indiqué dans l'illustration suivante :  
  
 ![Disposition conceptuelle d’un multiple&#45;tableau unidimensionnel](../cpp/media/vc38rc1.gif "vc38RC1")  
Disposition conceptuelle d'un tableau multidimensionnel  
  
 Dans les déclarations de tableaux multidimensionnels qui ont une liste d’initialiseurs (comme décrit dans [initialiseurs](../cpp/initializers.md)), l’expression constante qui spécifie les limites de la première dimension peut être omise. Par exemple :  
  
```  
// arrays2.cpp  
// compile with: /c  
const int cMarkets = 4;  
// Declare a float that represents the transportation costs.  
double TransportCosts[][cMarkets] = {   
   { 32.19, 47.29, 31.99, 19.11 },  
   { 11.29, 22.49, 33.47, 17.29 },  
   { 41.97, 22.09,  9.76, 22.55 }  
};  
```  
  
 La déclaration précédente définit un tableau composé de trois lignes et de quatre colonnes. Les lignes représentent les fabriques et les colonnes les marchés auxquels les fabriques livrent. Les valeurs sont les coûts de transport entre les fabriques et les marchés. La première dimension du tableau est omise, mais le compilateur la complète en examinant l'initialiseur.  
  
 Rubriques de cette section :  
  
-   [Utilisation des tableaux](../cpp/using-arrays-cpp.md)  
  
-   [Tableaux dans les expressions](../cpp/arrays-in-expressions.md)  
  
-   [Interprétation de l’opérateur d’indice](../cpp/interpretation-of-subscript-operator.md)  
  
-   [Indirection sur les types tableau](../cpp/indirection-on-array-types.md)  
  
-   [Tri des tableaux en C++](../cpp/ordering-of-cpp-arrays.md)  
  
## <a name="example"></a>Exemple  
 La technique d'omission des spécifications de limites de la première dimension d'un tableau multidimensionnel peut également être utilisée dans les déclarations de fonction comme suit :  
  
```  
// multidimensional_arrays.cpp  
// compile with: /EHsc  
// arguments: 3  
#include <limits>   // Includes DBL_MAX  
#include <iostream>  
  
const int cMkts = 4, cFacts = 2;  
  
// Declare a float that represents the transportation costs  
double TransportCosts[][cMkts] = {   
   { 32.19, 47.29, 31.99, 19.11 },  
   { 11.29, 22.49, 33.47, 17.29 },  
   { 41.97, 22.09,  9.76, 22.55 }    
};  
  
// Calculate size of unspecified dimension  
const int cFactories = sizeof TransportCosts /  
                  sizeof( double[cMkts] );  
  
double FindMinToMkt( int Mkt, double myTransportCosts[][cMkts], int mycFacts);  
  
using namespace std;  
  
int main( int argc, char *argv[] ) {  
   double MinCost;  
  
   if (argv[1] == 0) {  
      cout << "You must specify the number of markets." << endl;  
      exit(0);  
   }  
   MinCost = FindMinToMkt( *argv[1] - '0', TransportCosts, cFacts);  
   cout << "The minimum cost to Market " << argv[1] << " is: "  
       << MinCost << "\n";  
}  
  
double FindMinToMkt(int Mkt, double myTransportCosts[][cMkts], int mycFacts) {  
   double MinCost = DBL_MAX;  
  
   for( int i = 0; i < cFacts; ++i )  
      MinCost = (MinCost < TransportCosts[i][Mkt]) ?  
         MinCost : TransportCosts[i][Mkt];  
  
   return MinCost;  
}  
```  
  
```Output  
The minimum cost to Market 3 is: 17.29  
```  
  
## <a name="comments"></a>Commentaires  
 La fonction `FindMinToMkt` est écrite de telle sorte que l'ajout de nouvelles fabriques ne requiert aucune modification du code, juste une recompilation.  
  
## <a name="see-also"></a>Voir aussi  
 