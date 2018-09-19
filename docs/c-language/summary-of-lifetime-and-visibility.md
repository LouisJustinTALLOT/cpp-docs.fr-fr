---
title: Résumé de la durée de vie et de la visibilité | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
dev_langs:
- C++
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 6ef73c7e9592f1365e946d32d2aecc5894899316
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46061524"
---
# <a name="summary-of-lifetime-and-visibility"></a>Résumé de la durée de vie et de la visibilité

Le tableau suivant récapitule les caractéristiques de durée de vie et de visibilité pour la plupart des identificateurs. Les trois premières colonnes indiquent les attributs qui définissent la durée de vie et la visibilité. Un identificateur avec les attributs indiqués par les trois premières colonnes a la durée de vie et la visibilité affichées dans les quatrième et cinquième colonnes. Toutefois, le tableau ne traite pas tous les cas possibles. Pour plus d'informations, consultez [Classes de stockage](../c-language/c-storage-classes.md).

### <a name="summary-of-lifetime-and-visibility"></a>Résumé de la durée de vie et de la visibilité

|Attributs :<br /><br /> Niveau|Élément|Classe de stockage<br /><br /> Spécificateur|Résultat : <br /><br /> Durée de vie|Visibilité|
|---------------------------|----------|----------------------------------|--------------------------|----------------|
|Portée du fichier|Définition de variable|**static**|Global|Reste du fichier source dans lequel elle se produit|
||Déclaration de variable|**extern**|Global|Reste du fichier source dans lequel elle se produit|
||Définition ou prototype de fonction|**static**|Global|Fichier source unique|
||Prototype de fonction|**extern**|Global|Reste du fichier source|
|Portée de bloc|Déclaration de variable|**extern**|Global|Bloc|
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