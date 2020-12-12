---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1306'
title: Erreur des outils Éditeur de liens LNK1306
ms.date: 11/04/2016
f1_keywords:
- LNK1306
helpviewer_keywords:
- LNK1306
ms.assetid: fad1df6a-0bd9-412f-b0d1-7c9bc749c584
ms.openlocfilehash: aa6386da7c836eea8365d8a4ffde0bbd80d0fa81
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193654"
---
# <a name="linker-tools-error-lnk1306"></a>Erreur des outils Éditeur de liens LNK1306

> La fonction de point d’entrée DLL ne peut pas être gérée ; compiler en natif

`DllMain` ne peut pas être compilé en MSIL ; elle doit être compilée en natif.

Pour résoudre ce problème,

- Compilez le fichier qui contient le point d’entrée sans **/CLR**.

- Placez le point d’entrée dans une `#pragma unmanaged` section.

Pour plus d'informations, consultez les pages suivantes :

- [/CLR (compilation pour le Common Language Runtime)](../../build/reference/clr-common-language-runtime-compilation.md)

- [managé, non managé](../../preprocessor/managed-unmanaged.md)

- [Initialisation d’assemblys mixtes](../../dotnet/initialization-of-mixed-assemblies.md)

- [DLL et comportement de la bibliothèque runtime Visual C++](../../build/run-time-library-behavior.md)

## <a name="example"></a>Exemple

L’exemple suivant génère l’LNK1306.

```cpp
// LNK1306.cpp
// compile with: /clr /link /dll /entry:NewDllMain
// LNK1306 error expected
#include <windows.h>
int __stdcall NewDllMain( HINSTANCE h, ULONG ulReason, PVOID pvReserved ) {
   return 1;
}
```

Pour résoudre ce problème, n’utilisez pas l’option/CLR pour compiler ce fichier, ou utilisez une `#pragma` directive pour placer la définition du point d’entrée dans une section non managée, comme illustré dans cet exemple :

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
