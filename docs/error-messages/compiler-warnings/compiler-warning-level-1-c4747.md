---
title: Avertissement du compilateur (niveau 1) C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: ecaabd482049771b1d3915470a2be7a52e36d361
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50462385"
---
# <a name="compiler-warning-level-1-c4747"></a>Avertissement du compilateur (niveau 1) C4747

Appelant managé 'entrypoint' : Impossible d’exécuter du code managé le verrouillage du chargeur, y compris le point d’entrée DLL et les appels accessibles à partir du point d’entrée DLL

Le compilateur a détecté un point d’entrée DLL (probable) compilé en langage MSIL.  En raison de problèmes potentiels avec le chargement d’une DLL dont point d’entrée a été compilé en langage MSIL, il est vivement déconseillé de se compiler une fonction de point d’entrée DLL en langage MSIL.

Pour plus d’informations, consultez [l’initialisation des assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md) et [erreur des outils Éditeur de liens LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Ne compilez pas le module avec **/CLR**.

1. Marquez la fonction de point d’entrée avec `#pragma unmanaged`.

## <a name="example"></a>Exemple

L’exemple suivant génère C4747.

```
// C4747.cpp
// compile with: /clr /c /W1
// C4747 expected
#include <windows.h>

// Uncomment the following line to resolve.
// #pragma unmanaged

BOOL WINAPI DllMain(HANDLE hInstance, ULONG Command, LPVOID Reserved) {
   return TRUE;
};
```