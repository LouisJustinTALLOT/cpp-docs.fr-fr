---
description: 'En savoir plus sur : erreur du compilateur C3851'
title: Erreur du compilateur C3851
ms.date: 09/05/2018
f1_keywords:
- C3851
helpviewer_keywords:
- C3851
ms.assetid: da30c21c-33aa-4439-8fb3-2f5021ea4985
ms.openlocfilehash: 62f35b8828f7c8f1af9769152a88b7240ff9ff93
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97255364"
---
# <a name="compiler-error-c3851"></a>Erreur du compilateur C3851

> '*char*' : un nom de caractère universel ne peut pas désigner un caractère dans le jeu de caractères de base

## <a name="remarks"></a>Notes

Dans le code compilé en C++, vous ne pouvez pas utiliser un nom de caractère universel représentant un caractère dans le jeu de caractères source de base en dehors d’une chaîne ou d’un littéral de caractère. Pour plus d'informations, consultez [Character Sets](../../cpp/character-sets.md). Dans le code compilé en tant que C, vous ne pouvez pas utiliser un nom de caractère universel pour les caractères de la plage 0x20-0x7F, inclus, à l’exception de 0x24 (' $ '), 0x40 (' \@ ') ou 0x60 (' \` ').

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
