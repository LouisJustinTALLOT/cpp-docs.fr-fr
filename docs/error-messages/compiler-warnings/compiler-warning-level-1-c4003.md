---
title: Avertissement du compilateur (niveau 1) C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: 3bf1eea1b8ad0529d6603a2388e61b9107304f43
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80164740"
---
# <a name="compiler-warning-level-1-c4003"></a>Avertissement du compilateur (niveau 1) C4003

nombre de paramètres réels insuffisants pour la macro 'identificateur'

Le nombre de paramètres formels dans la définition de macro dépasse le nombre de paramètres réels dans la macro. L’expansion macro remplace le texte vide pour les paramètres manquants.

L’exemple suivant génère l’C4003 :

```cpp
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
