---
title: Erreur du compilateur C3851 | Microsoft Docs
ms.custom: ''
ms.date: 09/05/2018
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3851
dev_langs:
- C++
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e6d0f6da9c3295aa6a8fad4bf5dfd8e725424739
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46032477"
---
# <a name="compiler-error-c3851"></a>Erreur du compilateur C3851

> «*char*' : un nom de caractère universel ne peut pas désigner un caractère dans le jeu de caractères de base

## <a name="remarks"></a>Notes

Dans le code compilé en C++, vous ne pouvez pas utiliser un nom de caractère universel représentant un caractère dans le jeu de caractères source de base en dehors d’une chaîne ou d’un littéral de caractère. Pour plus d’informations, consultez [jeux de caractères](../../cpp/character-sets.md). Dans le code compilé en C, vous ne pouvez pas utiliser un nom de caractère universel pour les caractères dans la plage 0 x 20-0x7f, inclusivement, excepté pour 0 x 24 (« $»), 0 x 40 («\@»), ou 0 x 60 («\`»).

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