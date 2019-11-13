---
title: Avertissement du compilateur (niveau 1) C4747
ms.date: 11/04/2016
f1_keywords:
- C4747
helpviewer_keywords:
- C4747
ms.assetid: af37befd-ba1f-4bdc-96e1-a953f7a2ad9c
ms.openlocfilehash: 623b29d345a850cc312f23e4c521aa0be5b47242
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052445"
---
# <a name="compiler-warning-level-1-c4747"></a>Avertissement du compilateur (niveau 1) C4747

Appel de’EntryPoint’managé : le code managé ne peut pas être exécuté pendant le verrouillage du chargeur, y compris le point d’entrée de DLL et les appels atteints à partir du point d’entrée de DLL

Le compilateur a trouvé un point d’entrée de DLL (probable) compilé en MSIL.  En raison de problèmes potentiels liés au chargement d’une DLL dont le point d’entrée a été compilé en MSIL, il est fortement déconseillé de compiler une fonction de point d’entrée DLL en langage MSIL.

Pour plus d’informations, consultez [initialisation des assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md) et des outils de l' [éditeur de liens LNK1306](../../error-messages/tool-errors/linker-tools-error-lnk1306.md).

### <a name="to-correct-this-error"></a>Pour corriger cette erreur

1. Ne compilez pas le module avec **/CLR**.

1. Marquez la fonction de point d’entrée avec `#pragma unmanaged`.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4747.

```cpp
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