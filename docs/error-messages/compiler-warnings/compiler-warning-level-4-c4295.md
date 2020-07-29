---
title: Avertissement du compilateur (niveau 4) C4295
ms.date: 01/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: d960e5a5e2d7ad2d2b650095c42e9afea7bfe7fb
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87219870"
---
# <a name="compiler-warning-level-4-c4295"></a>Avertissement du compilateur (niveau 4) C4295

> '*Array*' : le tableau est trop petit pour contenir un caractère null de fin

Un tableau a été initialisé, mais le dernier caractère du tableau n’est pas null ; l’accès au tableau en tant que chaîne peut produire des résultats inattendus.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4295. Pour résoudre ce problème, vous pouvez déclarer la taille du tableau plus grande, pour contenir une valeur null de fin de la chaîne d’initialiseur, ou vous pouvez utiliser une liste d’initialiseurs de tableau pour clarifier l’intention qu’il s’agit d’un tableau de **`char`** , et non d’une chaîne terminée par le caractère null.

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
