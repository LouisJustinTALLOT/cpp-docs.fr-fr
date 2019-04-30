---
title: managé, non managé
ms.date: 11/04/2016
f1_keywords:
- vc-pragma.unmanaged
- managed_CPP
- unmanaged_CPP
- vc-pragma.managed
helpviewer_keywords:
- managed pragma
- pragmas, unmanaged
- pragmas, managed
- unmanaged pragma
ms.assetid: f072ddcc-e1ec-408a-8ce1-326ddb60e4a4
ms.openlocfilehash: 7fa1e3274b85faa9f3f72f4db5bf586ee5d8e274
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62409861"
---
# <a name="managed-unmanaged"></a>managé, non managé
Activez le contrôle au niveau de la fonction pour compiler les fonctions comme managées ou non managées.

## <a name="syntax"></a>Syntaxe

```
#pragma managed
#pragma unmanaged
#pragma managed([push,] on | off)
#pragma managed(pop)
```

## <a name="remarks"></a>Notes

Le [/CLR](../build/reference/clr-common-language-runtime-compilation.md) option du compilateur fournit le contrôle au niveau du module pour compiler les fonctions comme managées ou non managées.

Une fonction non managée est compilée pour la plateforme native et l'exécution de cette partie du programme est passée à la plateforme native par le Common Langage Runtime.

Les fonctions sont compilées comme managées par défaut lorsque l'option `/clr` est utilisée.

Quand vous appliquez ces pragmas :

- Ajoutez le pragma devant une fonction, et non dans un corps de fonction.

- Ajoutez le pragma après les instructions `#include`. N'utilisez pas ces pragmas avant les instructions `#include`.

Le compilateur ignore le **gérés** et **non managé** pragmas si `/clr` n’est pas utilisé dans la compilation.

Lorsqu'une fonction modèle est instanciée, l'état du pragma au moment de la définition du modèle détermine si elle est managée ou non managée.

Pour plus d’informations, consultez [l’initialisation des assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md).

## <a name="example"></a>Exemple

```cpp
// pragma_directives_managed_unmanaged.cpp
// compile with: /clr
#include <stdio.h>

// func1 is managed
void func1() {
   System::Console::WriteLine("In managed function.");
}

// #pragma unmanaged
// push managed state on to stack and set unmanaged state
#pragma managed(push, off)

// func2 is unmanaged
void func2() {
   printf("In unmanaged function.\n");
}

// #pragma managed
#pragma managed(pop)

// main is managed
int main() {
   func1();
   func2();
}
```

```Output
In managed function.
In unmanaged function.
```

## <a name="see-also"></a>Voir aussi

[Directives pragma et mot clé _Pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)