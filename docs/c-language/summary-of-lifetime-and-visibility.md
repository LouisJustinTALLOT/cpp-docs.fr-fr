---
title: "Résumé de la durée de vie et de la visibilité | Microsoft Docs"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-language
ms.tgt_pltfrm: 
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
caps.latest.revision: 
author: mikeblome
ms.author: mblome
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 1ee45ec7a2a842cc45c01c0e6f43ab49ba55aa3a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="summary-of-lifetime-and-visibility"></a>Résumé de la durée de vie et de la visibilité
Le tableau suivant récapitule les caractéristiques de durée de vie et de visibilité pour la plupart des identificateurs. Les trois premières colonnes indiquent les attributs qui définissent la durée de vie et la visibilité. Un identificateur avec les attributs indiqués par les trois premières colonnes a la durée de vie et la visibilité affichées dans les quatrième et cinquième colonnes. Toutefois, le tableau ne traite pas tous les cas possibles. Pour plus d'informations, consultez [Classes de stockage](../c-language/c-storage-classes.md).  
  
### <a name="summary-of-lifetime-and-visibility"></a>Résumé de la durée de vie et de la visibilité  
  
|Attributs :<br /><br /> Niveau|Élément|Classe de stockage<br /><br /> Spécificateur|Résultat : <br /><br /> Durée de vie|Visibilité|  
|---------------------------|----------|----------------------------------|--------------------------|----------------|  
|Portée du fichier|Définition de variable|**static**|Global|Reste du fichier source dans lequel elle se produit|  
||Déclaration de variable|`extern`|Global|Reste du fichier source dans lequel elle se produit|  
||Définition ou prototype de fonction|**static**|Global|Fichier source unique|  
||Prototype de fonction|`extern`|Global|Reste du fichier source|  
|Portée de bloc|Déclaration de variable|`extern`|Global|Bloc|  
||Définition de variable|**static**|Global|Bloc|  
||Définition de variable|**auto** ou **register**|Local|Bloc|  
  
## <a name="example"></a>Exemple  
  
### <a name="description"></a>Description  
 L'exemple suivant illustre les blocs, l'imbrication et la visibilité des variables :  
  
### <a name="code"></a>Code  
  
```  
// Lifetime_and_Visibility.c  
  
#include <stdio.h>  
  
int i = 1;  // i defined at external level  
  
int main()  // main function defined at external level  
{  
    printf_s( "%d\n", i ); // Prints 1 (value of external level i)  
    {                                 // Begin first nested block  
        int i = 2, j = 3;          // i and j defined at internal level  
        printf_s( "%d %d\n", i, j );  // Prints 2, 3  
        {                             // Begin second nested block  
            int i = 0;                // i is redefined  
            printf_s( "%d %d\n", i, j ); // Prints 0, 3  
        }                             // End of second nested block  
        printf_s( "%d\n", i );        // Prints 2 (outer definition  
                                      //  restored)  
    }                                 // End of first nested block  
    printf_s( "%d\n", i );            // Prints 1 (external level  
                                      // definition restored)  
    return 0;  
}   
```  
  
### <a name="comments"></a>Commentaires  
 Dans cet exemple, il existe quatre niveaux de visibilité : le niveau externe et trois niveaux de bloc. Les valeurs sont imprimées à l'écran comme indiqué dans les commentaires suivant chaque instruction.  
  
## <a name="see-also"></a>Voir aussi  
 [Durée de vie, portée, visibilité et liaison](../c-language/lifetime-scope-visibility-and-linkage.md)