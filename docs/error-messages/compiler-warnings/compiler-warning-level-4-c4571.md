---
title: Avertissement du compilateur (niveau 4) C4571
description: Documente l’avertissement du compilateur Microsoft C++ C4571.
ms.date: 08/24/2020
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 35f2b30a8ab7cfcc27ed7aae3aedd9bc81efacc8
ms.sourcegitcommit: efc8c32205c9d610f40597556273a64306dec15d
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/26/2020
ms.locfileid: "88898552"
---
# <a name="compiler-warning-level-4-c4571"></a>Avertissement du compilateur (niveau 4) C4571

> Informations : la `catch(...)` sémantique a changé depuis Visual C++ 7,1 ; les exceptions structurées (SEH) ne sont plus interceptées

C4571 est généré pour chaque `catch(...)` bloc lorsque vous spécifiez l' **`/EHs`** option de compilateur.

## <a name="remarks"></a>Notes

Lorsque vous spécifiez l' **`/EHs`** option de compilateur, les `catch(...)` blocs n’interceptent pas les exceptions structurées. (Division par zéro, ou exceptions de pointeur null, par exemple). Un `catch(...)` bloc intercepte uniquement les exceptions C++ levées explicitement. Pour plus d’informations, consultez l’article [Gestion des exceptions](../../cpp/exception-handling-in-visual-cpp.md).

Cet avertissement est désactivé par défaut.  Activez cet avertissement pour vous assurer que lorsque vous compilez avec **`/EHs`** vos `catch (...)` blocs, n’interceptez pas les exceptions structurées. Pour plus d’informations, consultez [avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md).

Vous pouvez résoudre C4571 de l’une des manières suivantes :

- Compilez avec **`/EHa`** si vous souhaitez toujours que vos `catch(...)` blocs interceptent les exceptions structurées.

- N’activez pas C4571 si vous ne souhaitez pas que vos `catch(...)` blocs interceptent des exceptions structurées, mais que vous souhaitez toujours utiliser des `catch(...)` blocs.  Vous pouvez toujours intercepter des exceptions structurées à l’aide des mots clés de gestion structurée des exceptions ( **`__try`** , **`__except`** et **`__finally`** ).  Toutefois, n’oubliez pas que, lorsqu’il est compilé à l’aide **`/EHs`** de, les destructeurs sont appelés uniquement quand une exception C++ est levée, et non lorsqu’une exception SEH se produit.

- Remplacez `catch(...)` les blocs par des blocs catch pour des exceptions c++ spécifiques et ajoutez éventuellement une gestion structurée des exceptions autour de la gestion des exceptions c++ ( **`__try`** , **`__except`** et **`__finally`** ).   Pour plus d’informations, consultez [gestion structurée des exceptions (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) et [ `/EH` (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4571.

```cpp
// C4571.cpp
// compile with: /EHs /W4 /c
#pragma warning(default : 4571)
int main() {
   try {
      int i = 0, j = 1;
      j /= i;   // this will throw a SE (divide by zero)
   }
   catch(...) {}   // C4571 warning
}
```
