---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4514'
title: Avertissement du compilateur (niveau 4) C4514
ms.date: 11/04/2016
f1_keywords:
- C4514
helpviewer_keywords:
- C4514
ms.assetid: cdae966a-9cd4-4e31-af30-2a014e68f614
ms.openlocfilehash: 5d0ba77f6e2d2f0288f92994f0daffde36545c27
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97241220"
---
# <a name="compiler-warning-level-4-c4514"></a>Avertissement du compilateur (niveau 4) C4514

'fonction' : la fonction inline non référencée a été supprimée

L’optimiseur a supprimé une fonction inline qui n’est pas appelée.

Cet avertissement est désactivé par défaut. Consultez [Avertissements du compilateur désactivés par défaut](../../preprocessor/compiler-warnings-that-are-off-by-default.md) pour plus d'informations.

L’exemple suivant génère l’C4514 :

```cpp
// C4514.cpp
// compile with: /W4
#pragma warning(default : 4514)
class A
{
   public:
      void func()   // C4514, remove the function to resolve
      {
      }
};

int main()
{
}
```
