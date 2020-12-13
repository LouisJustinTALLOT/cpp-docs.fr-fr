---
description: 'En savoir plus sur : pragmas managés, non managés'
title: managed, unmanaged, pragmas
ms.date: 08/29/2019
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
ms.openlocfilehash: 10f632b009c9922f67f4321acc862142d895e7ae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97333391"
---
# <a name="managed-unmanaged-pragmas"></a>managed, unmanaged, pragmas

Activez le contrôle au niveau de la fonction pour compiler des fonctions comme managées ou non managées.

## <a name="syntax"></a>Syntaxe

> **gérée par #pragma**\
> **#pragma non géré**\
> **#pragma géré (** [ **push,** ] { **on**  |  **off** } **)**\
> **#pragma géré (POP)**

## <a name="remarks"></a>Notes

L’option du compilateur [/CLR](../build/reference/clr-common-language-runtime-compilation.md) fournit un contrôle au niveau du module pour la compilation des fonctions comme gérées ou non managées.

Une fonction non managée sera compilée pour la plateforme native. L’exécution de cette partie du programme sera transmise à la plateforme native par le common language runtime.

Les fonctions sont compilées comme managées par défaut lorsque l'option `/clr` est utilisée.

Quand vous appliquez ces pragmas :

- Ajoutez le pragma précédant une fonction, mais pas dans le corps d’une fonction.

- Ajoutez le pragma après les instructions `#include`. N’utilisez pas ces pragmas avant les `#include` instructions.

Le compilateur ignore les pragmas **managés** et **non managés** si `/clr` n’est pas utilisé dans la compilation.

Quand une fonction de modèle est instanciée, l’état du pragma lorsque le modèle est défini détermine s’il est managé ou non managé.

Pour plus d’informations, consultez [initialisation des assemblys mixtes](../dotnet/initialization-of-mixed-assemblies.md).

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

[Directives Pragma et mot clé __pragma](../preprocessor/pragma-directives-and-the-pragma-keyword.md)
