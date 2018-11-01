---
title: Nettoyage des ressources
ms.date: 11/04/2016
helpviewer_keywords:
- termination handlers [C++], cleaning up resources
- exception handling [C++], cleaning up resources
- C++ exception handling, termination handlers
- resources [C++], cleaning up
- exception handling [C++], cleanup code
- try-catch keyword [C++], termination handlers
ms.assetid: 65753efe-6a27-4750-b90c-50635775c1b6
ms.openlocfilehash: 0db21b20b94dc1a3f347bd848c999a961398759b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50575693"
---
# <a name="cleaning-up-resources"></a>Nettoyage des ressources

Pendant l'exécution du gestionnaire de terminaisons, il est possible que vous ne sachiez pas quelles ressources ont été réellement allouées avant l'appel du gestionnaire de terminaisons. Il est possible que le **__try** bloc d’instructions a été interrompu avant que toutes les ressources ont été alloués, afin que pas toutes les ressources ont été ouverts.

Ainsi, par sécurité, vous devez vérifier les ressources qui sont réellement ouvertes avant de procéder au nettoyage de la gestion du bloc de fin. Voici une procédure recommandée :

1. Initialiser les handles sur NULL.

1. Dans le **__try** instruction de blocs, d’allouer des ressources. Les handles sont définis sur des valeurs positives lorsque la ressource est allouée.

1. Dans le **__finally** bloc d’instructions, libérez chaque ressource dont handle correspondant ou la variable d’indicateur est différente de zéro, ou not NULL.

## <a name="example"></a>Exemple

Par exemple, le code suivant utilise un gestionnaire de terminaisons pour fermer trois fichiers et un bloc de mémoire alloués lors de la **__try** bloc d’instructions. Avant de nettoyer une ressource, le code vérifie si elle a été allouée.

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

[Écriture d’un gestionnaire de terminaisons](../cpp/writing-a-termination-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)