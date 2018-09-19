---
title: Compilateur avertissement (niveau 1) C4584 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4584
dev_langs:
- C++
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9db97bf35034f7ca628f860924bfb9a1fccc942f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46036252"
---
# <a name="compiler-warning-level-1-c4584"></a>Avertissement du compilateur (niveau 1) C4584

'classe1' : classe de base 'classe2' est déjà une classe de base de 'class3'

La classe que vous avez défini hérite de deux classes, dont hérite de l’autre. Exemple :

```
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

Dans ce cas, un avertissement est émis sur la classe C, car il hérite de la classe A et de la classe B, laquelle hérite également de la classe A. Cet avertissement sert un rappel que vous devez qualifier complètement l’utilisation de membres à partir de ces classes de base ou une erreur du compilateur est générée en raison de l’ambiguïté quant au membre de classe auquel vous faites référence.