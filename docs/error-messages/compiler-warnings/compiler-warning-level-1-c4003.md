---
title: Compilateur avertissement (niveau 1) C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: 7b1b87c643111f2b12124e348be8fb823e113937
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62187304"
---
# <a name="compiler-warning-level-1-c4003"></a>Compilateur avertissement (niveau 1) C4003

nombre de paramètres réels insuffisants pour la macro 'identificateur'

Le nombre de paramètres formels dans la définition de macro dépasse le nombre de paramètres réels dans la macro. Expansion macro substitue un texte vide pour les paramètres manquants.

L’exemple suivant génère C4003 :

```
// C4003.cpp
// compile with: /WX
#define test(a,b) (a+b)

int main()
{
   int a = 1;
   int b = 2;
   a = test(b);   // C4003
   // try..
   a = test(a,b);
}
```