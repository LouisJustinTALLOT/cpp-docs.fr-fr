---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4584'
title: Avertissement du compilateur (niveau 1) C4584
ms.date: 11/04/2016
f1_keywords:
- C4584
helpviewer_keywords:
- C4584
ms.assetid: ad86582f-cb8c-4d21-8c4c-a6c800059e25
ms.openlocfilehash: 32a6b797f7fb0cf2c1a087999c8172e11686e27b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281624"
---
# <a name="compiler-warning-level-1-c4584"></a>Avertissement du compilateur (niveau 1) C4584

'classe1 ' : la classe de base’classe2 'est déjà une classe de base de’class3 '

La classe que vous avez définie hérite de deux classes, dont l’une hérite de l’autre. Par exemple :

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
