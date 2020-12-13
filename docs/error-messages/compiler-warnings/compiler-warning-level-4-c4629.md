---
description: 'En savoir plus sur : avertissement du compilateur (niveau 4) C4629'
title: Avertissement du compilateur (niveau 4) C4629
ms.date: 11/04/2016
f1_keywords:
- C4629
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
ms.openlocfilehash: b357b72ca95682c33d3f4019d4663593c5c5ee8d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134171"
---
# <a name="compiler-warning-level-4-c4629"></a>Avertissement du compilateur (niveau 4) C4629

digrammes utilisés, séquence de caractères 'digramme' interprétée comme jeton 'caractère' (insérez un espace entre les deux caractères si cela n’est pas ce que vous souhaitiez)

Sous [/Za](../../build/reference/za-ze-disable-language-extensions.md), le compilateur vous avertit quand il détecte un digramme.

L’exemple suivant génère l’avertissement C4629 :

```cpp
// C4629.cpp
// compile with: /Za /W4
int main()
<%   // C4629 <% digraph for {
}
```
