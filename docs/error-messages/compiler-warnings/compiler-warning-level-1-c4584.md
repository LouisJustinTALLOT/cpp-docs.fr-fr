---
title: Avertissement du compilateur (niveau 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 831789f5295fcf91e83de3bd0bba12c8429e9fa3
ms.sourcegitcommit: e5192a25c084eda9eabfa37626f3274507e026b3
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/12/2019
ms.locfileid: "73966232"
---
# <a name="compiler-warning-level-1-c4584"></a>Avertissement du compilateur (niveau 1) C4584

'classe1 ' : la classe de base’classe2 'est déjà une classe de base de’class3 '

La classe que vous avez définie hérite de deux classes, dont l’une hérite de l’autre. Exemple :

```cpp
// C4584.cpp
// compile with: /W1 /LD
class A {
};

class B : public A {
};

class C : public A, public B { // C4584
};
```

Dans ce cas, un avertissement est émis sur la classe C, car il hérite à la fois de la classe A et de la classe B, qui hérite également de la classe A. Cet avertissement vous rappelle que vous devez qualifier complètement l’utilisation des membres à partir de ces classes de base, sinon une erreur du compilateur sera générée en raison de l’ambiguïté en ce qui concerne le membre de classe auquel vous faites référence.