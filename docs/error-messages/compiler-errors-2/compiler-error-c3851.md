---
title: Erreur du compilateur C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 52c4f3a393ffaf2b61a65c8e2e0dcc8efac08288
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62380940"
---
# <a name="compiler-error-c3851"></a>Erreur du compilateur C3851

> «*char*' : un nom de caractère universel ne peut pas désigner un caractère dans le jeu de caractères de base

## <a name="remarks"></a>Notes

Dans le code compilé en C++, vous ne pouvez pas utiliser un nom de caractère universel représentant un caractère dans le jeu de caractères source de base en dehors d’une chaîne ou d’un littéral de caractère. Pour plus d’informations, consultez [Character Sets](../../cpp/character-sets.md). Dans le code compilé en C, vous ne pouvez pas utiliser un nom de caractère universel pour les caractères dans la plage 0 x 20-0x7f, inclusivement, excepté pour 0 x 24 (« $»), 0 x 40 («\@»), ou 0 x 60 («\`»).

## <a name="example"></a>Exemple

Les exemples suivants génèrent C3851 et montrent comment résoudre le problème :

```cpp
// C3851.cpp
int main()
{
   int test1_\u0041 = 0;   // C3851, \u0041 = 'A' in basic character set
   int test2_A = 0;        // OK
}
```