---
title: Erreur du compilateur C3174
ms.date: 11/04/2016
f1_keywords:
- C3174
helpviewer_keywords:
- C3174
ms.assetid: fe6b3b5a-8196-485f-a45f-0b2e51df4086
ms.openlocfilehash: a14b59168e0723ea25eefa9ec33a3131837a3aa4
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91508276"
---
# <a name="compiler-error-c3174"></a>Erreur du compilateur C3174

l’attribut module n’a pas été spécifié

Un programme qui utilise des attributs Visual C++ n’utilise pas non plus l’attribut [module](../../windows/attributes/module-cpp.md) , qui est requis dans tout programme qui utilise des attributs.

L’exemple suivant génère l’C3174 :

```cpp
// C3174.cpp
// C3174 expected
// uncomment the following line to resolve this C3174
// [module(name="x")];
[export]
struct S
{
   int i;
};

int main()
{
}
```
