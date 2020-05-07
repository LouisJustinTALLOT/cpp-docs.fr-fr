---
title: Résumé de la durée de vie et de la visibilité
ms.date: 11/04/2016
helpviewer_keywords:
- lifetime, and visibility
- visibility, identifiers
ms.assetid: ea05a253-7658-482c-9a6b-abd71169c42d
ms.openlocfilehash: f364c3c0b558c00e3d411ab5b697ed01ec395cbd
ms.sourcegitcommit: a5fa9c6f4f0c239ac23be7de116066a978511de7
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/20/2019
ms.locfileid: "75299076"
---
# <a name="summary-of-lifetime-and-visibility"></a>Résumé de la durée de vie et de la visibilité

Le tableau suivant récapitule les caractéristiques de durée de vie et de visibilité pour la plupart des identificateurs. Les trois premières colonnes indiquent les attributs qui définissent la durée de vie et la visibilité. Un identificateur avec les attributs indiqués par les trois premières colonnes a la durée de vie et la visibilité affichées dans les quatrième et cinquième colonnes. Toutefois, le tableau ne traite pas tous les cas possibles. Pour plus d'informations, consultez [Classes de stockage](../c-language/c-storage-classes.md).

### <a name="summary-of-lifetime-and-visibility"></a>Résumé de la durée de vie et de la visibilité

|Attributs :<br /><br /> Level|Élément|Classe de stockage<br /><br /> Spécificateur|Résultat :<br /><br /> Durée de vie|Visibilité|
|---------------------------|----------|----------------------------------|--------------------------|----------------|
|Portée du fichier|Définition de variable|**statique**|Globale|Reste du fichier source dans lequel elle se produit|
||Déclaration de variable|**extern**|Globale|Reste du fichier source dans lequel elle se produit|
||Définition ou prototype de fonction|**statique**|Globale|Fichier source unique|
||Prototype de fonction|**extern**|Globale|Reste du fichier source|
|Portée de bloc|Déclaration de variable|**extern**|Globale|Bloquer|
||Définition de variable|**statique**|Globale|Bloquer|
||Définition de variable|**auto** ou **register**|Local|Bloquer|

## <a name="example"></a> Exemple

### <a name="description"></a>Description

L'exemple suivant illustre les blocs, l'imbrication et la visibilité des variables :

### <a name="code"></a>Code

```c
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
