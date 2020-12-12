---
description: 'En savoir plus sur : erreur du compilateur C3446'
title: Erreur du compilateur C3446
ms.date: 07/21/2017
f1_keywords:
- C3446
helpviewer_keywords:
- C3446
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
ms.openlocfilehash: 442ac07c1684278e76f86531d1c28de6507eb999
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113665"
---
# <a name="compiler-error-c3446"></a>Erreur du compilateur C3446

>'*Class*' : un initialiseur de membre par défaut n’est pas autorisé pour un membre d’une classe value

Dans Visual Studio 2015 et antérieur, le compilateur autorisait (mais ignorait) un initialiseur de membre par défaut pour un membre d’une classe value. L’initialisation par défaut d’une classe value initialise systématiquement les membres à zéro ; un constructeur par défaut n’est pas autorisé. Dans Visual Studio 2017, les initialiseurs de membres par défaut déclenchent une erreur de compilateur, comme illustré dans cet exemple :

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3446 dans Visual Studio 2017 et versions ultérieures :

```cpp
// C3446.cpp
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer
                  // is not allowed for a member of a value class
       int j {0}; // C3446
};
```

Pour corriger l’erreur, supprimez l’initialiseur :

```cpp
// C3446b.cpp
value struct V
{
       int i;
       int j;
};
```
