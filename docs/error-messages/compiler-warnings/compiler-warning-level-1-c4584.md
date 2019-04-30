---
title: Avertissement du compilateur (niveau 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 3c60575e766ea3490a40711fe26c3e402c41fbdd
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62397248"
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