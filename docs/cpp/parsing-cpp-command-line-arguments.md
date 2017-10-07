---
title: Analyse des Arguments de ligne de commande C++ | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- quotation marks, command-line arguments
- double quotation marks
- command line [C++], parsing
- parsing, command-line arguments
- startup code, parsing command-line arguments
ms.assetid: e634e733-ac2f-4298-abe2-7e9288c94951
caps.latest.revision: 8
author: mikeblome
ms.author: mblome
manager: ghogen
ms.translationtype: HT
ms.sourcegitcommit: 6ffef5f51e57cf36d5984bfc43d023abc8bc5c62
ms.openlocfilehash: 5d3fbcd6b4e92d6e445d78a1b36efae319e472d7
ms.contentlocale: fr-fr
ms.lasthandoff: 09/25/2017

---
# <a name="parsing-c-command-line-arguments"></a>Analyse des arguments de ligne de commande C++
**Section spécifique à Microsoft**  
  
 Code de démarrage Microsoft C/C++ utilise les règles suivantes lors de l’interprétation des arguments spécifiés sur la ligne de commande du système d’exploitation :  
  
-   Les arguments sont délimités par un espace blanc, qui peut être un espace ou une tabulation.  
  
-   Le signe insertion (^) n’est pas reconnu comme caractère d’échappement ni comme délimiteur. Le caractère est géré complètement par l’Analyseur de ligne de commande du système d’exploitation avant d’être passé à la `argv` tableau dans le programme.  
  
-   Une chaîne placée entre guillemets doubles («*chaîne*») est interprétée comme un argument unique, quel que soit le contenu dans un espace blanc. Une chaîne entre guillemets peut être incorporée dans un argument.  
  
-   Un guillemet double précédé d’une barre oblique inverse (\\") est interprété comme un caractère guillemet double littéral (").  
  
-   Les barres obliques inverses sont interprétées littéralement, sauf si elles précèdent immédiatement un guillemet double.  
  
-   Si un nombre pair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le `argv` tableau pour chaque paire de barres obliques inverses et le guillemet double est interprété comme un délimiteur de chaîne.  
  
-   Si un nombre impair de barres obliques inverses est suivi d’un guillemet double, une barre oblique inverse est placée dans le `argv` tableau pour chaque paire de barres obliques inverses et le guillemet double est « échappé » à la barre oblique inverse restante, provoquant un guillemet double littéral ( » ) doit être placé dans `argv`.  
  
## <a name="example"></a>Exemple  
 Le programme suivant montre les arguments de la ligne de commande sont passés :  
  
```  
// command_line_arguments.cpp  
// compile with: /EHsc  
#include <iostream>  
  
using namespace std;  
int main( int argc,      // Number of strings in array argv  
          char *argv[],   // Array of command-line argument strings  
          char *envp[] )  // Array of environment variable strings  
{  
    int count;  
  
    // Display each command-line argument.  
    cout << "\nCommand-line arguments:\n";  
    for( count = 0; count < argc; count++ )  
         cout << "  argv[" << count << "]   "  
                << argv[count] << "\n";  
}  
```  
  
 Le tableau suivant montre l’exemple d’entrée et sortie attendue, qui montre les règles dans la liste précédente.  
  
### <a name="results-of-parsing-command-lines"></a>Résultats de l’analyse des lignes de commande  
  
|Entrée sur la ligne de commande|argv[1]|argv[2]|argv[3]|  
|-------------------------|---------------|---------------|---------------|  
|`"abc" d e`|`abc`|`d`|`e`|  
|`a\\b d"e f"g h`|`a\\b`|`de fg`|`h`|  
|`a\\\"b c d`|`a\"b`|`c`|`d`|  
|`a\\\\"b c" d e`|`a\\b c`|`d`|`e`|  
  
**FIN de la section spécifique à Microsoft**  
  
## <a name="see-also"></a>Voir aussi  
 [main : démarrage du programme](../cpp/main-program-startup.md)
