---
title: Avertissement du compilateur (niveau 4) C4571
ms.date: 11/04/2016
f1_keywords:
- C4571
helpviewer_keywords:
- C4571
ms.assetid: 07aa17bd-b15c-4266-824c-57cc445e8edd
ms.openlocfilehash: 4fe99e12c5d2dfb725e1e4aa0ac2fb0b1ccb4f28
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219883"
---
# <a name="compiler-warning-level-4-c4571"></a>Avertissement du compilateur (niveau 4) C4571

Informations : la sémantique catch (...) a changé depuis Visual C++ 7,1 ; les exceptions structurées (SEH) ne sont plus interceptées

C4571 est généré pour chaque bloc catch (...) lors de la compilation avec **/EHS**.

Lors de la compilation avec **/EHS**, un bloc catch (...) n’intercepte pas une exception structurée (division par zéro, pointeur null, par exemple); un bloc catch (...) intercepte uniquement les exceptions C++ levées explicitement.  Pour plus d’informations, consultez l’article [Gestion des exceptions](../../cpp/exception-handling-in-visual-cpp.md).

Cet avertissement est désactivé par défaut.  Activez cet avertissement pour vous assurer que, quand vous compilez avec **/EHS** , vos blocs catch (...) n’envisagent pas d’intercepter des exceptions structurées.  Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

Vous pouvez résoudre C4571 de l’une des manières suivantes :

- Compilez avec **/EHa** si vous souhaitez toujours que vos blocs catch (...) interceptent les exceptions structurées.

- N’activez pas C4571 si vous ne souhaitez pas que vos blocs catch (...) interceptent des exceptions structurées, mais que vous souhaitez toujours utiliser des blocs catch (...).  Vous pouvez toujours intercepter des exceptions structurées à l’aide des mots clés de gestion des exceptions structurées (**__try**, **`__except`** et **`__finally`** ).  Toutefois, n’oubliez pas que lorsque les destructeurs **/EHS** compilés sont appelés uniquement quand une exception C++ est levée, et non lorsqu’une exception SEH se produit.

- Remplacez le bloc catch (...) par des blocs catch pour des exceptions C++ spécifiques et ajoutez éventuellement une gestion structurée des exceptions autour de la gestion des exceptions C++ (**__try**, **`__except`** et **`__finally`** ).  Pour plus d’informations, consultez [gestion structurée des exceptions (C/C++)](../../cpp/structured-exception-handling-c-cpp.md) .

Pour plus d’informations [, consultez/Eh (modèle de gestion des exceptions)](../../build/reference/eh-exception-handling-model.md) .

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
