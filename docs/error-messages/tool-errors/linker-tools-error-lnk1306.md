---
title: Erreur des outils Éditeur de liens LNK1306
ms.date: 11/04/2016
f1_keywords:
- LNK1306
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
ms.openlocfilehash: ddaa8797e0cf8ff617408aedc770b21cc656cec4
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62160456"
---
# <a name="linker-tools-error-lnk1306"></a>Erreur des outils Éditeur de liens LNK1306

> Fonction de point d’entrée DLL ne peut pas être gérée ; compilez en natif

`DllMain` ne peut pas être compilée en langage MSIL ; Il doit être compilé en natif.

Pour résoudre ce problème,

- Compilez le fichier qui contient le point d’entrée sans **/CLR**.

- Placez le point d’entrée dans un `#pragma unmanaged` section.

Pour plus d'informations, voir :

- [/clr (Compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [managed, unmanaged](../../preprocessor/managed-unmanaged.md)

- [Initialisation d’assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md)

- [DLL et comportement de la bibliothèque runtime Visual C++](../../build/run-time-library-behavior.md)

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur LNK1306.

```cpp
// LNK1306.cpp
// compile with: /clr /link /dll /entry:NewDllMain
// LNK1306 error expected
#include <windows.h>
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
```

Pour résoudre ce problème, n’utilisez pas l’option/CLR pour compiler ce fichier, ou utiliser un `#pragma` directive pour placer la définition de point d’entrée dans une section non managée comme indiqué dans cet exemple :

```cpp
// LNK1306fix.cpp
// compile with: /clr /link /dll /entry:NewDllMain
#include <windows.h>
#pragma managed(push, off)
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
#pragma managed(pop)
```
