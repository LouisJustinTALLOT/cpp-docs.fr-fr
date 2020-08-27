---
title: Nettoyage des ressources
description: Comment libérer des ressources pendant un gestionnaire de terminaisons pour la gestion structurée des exceptions.
ms.date: 08/24/2020
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
ms.openlocfilehash: dae92a515db25b9985a890d7d08cc213f88ecfea
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898438"
---
# <a name="cleaning-up-resources"></a>Nettoyage des ressources

Pendant l’exécution du gestionnaire de terminaisons, vous ne savez peut-être pas quelles ressources ont été acquises avant l’appel du gestionnaire de terminaisons. Il est possible que le **`__try`** bloc d’instructions ait été interrompu avant que toutes les ressources n’aient été acquises, de sorte que toutes les ressources n’ont pas été ouvertes.

Pour être sûr, vous devez vérifier les ressources qui sont ouvertes avant de procéder au nettoyage de la gestion des arrêts. Voici une procédure recommandée :

1. Initialiser les handles sur NULL.

1. Dans le **`__try`** bloc d’instructions, acquérir des ressources. Les handles sont définis sur des valeurs positives au fur et à mesure que la ressource est acquise.

1. Dans le **`__finally`** bloc d’instructions, libérez chaque ressource dont la variable de handle ou d’indicateur correspondante est différente de zéro ou non null.

## <a name="example"></a>Exemple

Par exemple, le code suivant utilise un gestionnaire de terminaison pour fermer trois fichiers et libérer un bloc de mémoire. Ces ressources ont été acquises dans le **`__try`** bloc d’instructions. Avant de nettoyer une ressource, le code vérifie d’abord si la ressource a été acquise.

```cpp
// exceptions_Cleaning_up_Resources.cpp
#include <stdlib.h>
#include <malloc.h>
#include <stdio.h>
#include <windows.h>

void fileOps() {
   FILE  *fp1 = NULL,
         *fp2 = NULL,
         *fp3 = NULL;
   LPVOID lpvoid = NULL;
   errno_t err;

   __try {
      lpvoid = malloc( BUFSIZ );

      err = fopen_s(&fp1, "ADDRESS.DAT", "w+" );
      err = fopen_s(&fp2, "NAMES.DAT", "w+" );
      err = fopen_s(&fp3, "CARS.DAT", "w+" );
   }
   __finally {
      if ( fp1 )
         fclose( fp1 );
      if ( fp2 )
         fclose( fp2 );
      if ( fp3 )
         fclose( fp3 );
      if ( lpvoid )
         free( lpvoid );
   }
}

int main() {
   fileOps();
}
```

## <a name="see-also"></a>Voir aussi

[Écriture d’un gestionnaire des arrêts](../cpp/writing-a-termination-handler.md)<br/>
[Structured Exception Handling (C/C++)](../cpp/structured-exception-handling-c-cpp.md)
