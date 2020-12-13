---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4003'
title: Avertissement du compilateur (niveau 1) C4003
ms.date: 11/04/2016
f1_keywords:
- C4003
helpviewer_keywords:
- C4003
ms.assetid: 0ed1c285-4428-4c90-8131-86897e31f115
ms.openlocfilehash: d8a581e9cf6152a3e0e92832b36e5f61a94277f1
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97335986"
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
