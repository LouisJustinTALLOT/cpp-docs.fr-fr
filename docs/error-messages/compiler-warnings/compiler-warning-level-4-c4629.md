---
title: Compilateur avertissement (niveau 4) C4629 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4629
dev_langs:
- C++
helpviewer_keywords:
- C4629
ms.assetid: 158cde12-bae5-4d43-b575-b52b35aaa0b9
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: e5f728d60a654a672002610d41aa4e387b4479e0
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46081316"
---
# <a name="compiler-warning-level-4-c4629"></a>Avertissement du compilateur (niveau 4) C4629

digrammes utilisés, séquence de caractères 'digramme' interprétée comme jeton 'caractère' (insérez un espace entre les deux caractères si cela n’est pas ce que vous souhaitiez)

Sous [/Za](../../build/reference/za-ze-disable-language-extensions.md), le compilateur vous avertit quand il détecte un digramme.

L’exemple suivant génère l’avertissement C4629 :

```
// C4629.cpp
// compile with: /Za /W4
int main()
<%   // C4629 <% digraph for {
}
```