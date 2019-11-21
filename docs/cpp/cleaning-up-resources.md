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
ms.openlocfilehash: 225c3ccaf3342f11ad4eb6d6575ad3ac542acfd2
ms.sourcegitcommit: 654aecaeb5d3e3fe6bc926bafd6d5ace0d20a80e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/20/2019
ms.locfileid: "74246646"
---
# <a name="cleaning-up-resources"></a>Nettoyage des ressources

Pendant l'exécution du gestionnaire de terminaisons, il est possible que vous ne sachiez pas quelles ressources ont été réellement allouées avant l'appel du gestionnaire de terminaisons. It is possible that the **__try** statement block was interrupted before all resources were allocated, so that not all resources were opened.

Ainsi, par sécurité, vous devez vérifier les ressources qui sont réellement ouvertes avant de procéder au nettoyage de la gestion du bloc de fin. Voici une procédure recommandée :

1. Initialiser les handles sur NULL.

1. In the **__try** statement block, allocate resources. Les handles sont définis sur des valeurs positives lorsque la ressource est allouée.

1. In the **__finally** statement block, release each resource whose corresponding handle or flag variable is nonzero or not NULL.

## <a name="example"></a>Exemple

For example, the following code uses a termination handler to close three files and a memory block that were allocated in the **__try** statement block. Avant de nettoyer une ressource, le code vérifie si elle a été allouée.

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

[Writing a termination handler](../cpp/writing-a-termination-handler.md)<br/>
[Gestion structurée des exceptions (C/C++)](../cpp/structured-exception-handling-c-cpp.md)