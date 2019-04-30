---
title: Avertissement du compilateur (niveau 4) C4295
ms.date: 1/09/2018
f1_keywords:
- C4295
helpviewer_keywords:
- C4295
ms.assetid: 20dbff85-9f62-4ca3-8fe9-079d4512006d
ms.openlocfilehash: ed31ea19f9c36a9c6fab7452a4bfc3843a151059
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62400875"
---
# <a name="compiler-warning-level-4-c4295"></a>Avertissement du compilateur (niveau 4) C4295

> «*tableau*' : tableau est trop petit pour comporter un caractère null de fin

Un tableau a été initialisé mais le dernier caractère dans le tableau n’est pas une valeur null ; accès au tableau sous forme de chaîne peut produire des résultats inattendus.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4295. Pour résoudre ce problème, vous pouvez déclarer la taille du tableau plus grand pour contenir un caractère null de fin de la chaîne de l’initialiseur, ou vous pouvez utiliser une liste d’initialiseurs de tableau pour rendre l’intention clair qu’il s’agit d’un tableau de `char`, pas une chaîne se terminant par null.

```C
// C4295.c
// compile with: /W4

int main() {
   char a[3] = "abc";           // C4295
   char b[3] = {'d', 'e', 'f'}; // No warning
   a[0] = b[2];
}
```
