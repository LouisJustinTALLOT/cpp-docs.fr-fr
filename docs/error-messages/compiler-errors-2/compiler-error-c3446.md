---
title: Erreur du compilateur C3446 | Microsoft Docs
ms.custom: ''
ms.date: 07/21/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3446
dev_langs:
- C++
helpviewer_keywords:
- C3445
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a88bb77489d2596c271842e7becb0214d1af2821
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46018861"
---
# <a name="compiler-error-c3446"></a>Erreur du compilateur C3446

>«*classe*' : un initialiseur de membre par défaut n’est pas autorisé pour un membre d’une classe value

Dans Visual Studio 2015 et antérieur, le compilateur autorisait (mais ignorait) un initialiseur de membre par défaut pour un membre d’une classe value. L’initialisation par défaut d’une classe value initialise systématiquement les membres à zéro ; un constructeur par défaut n’est pas autorisé. Dans Visual Studio 2017, les initialiseurs de membres par défaut déclenchent une erreur de compilateur, comme illustré dans cet exemple :

## <a name="example"></a>Exemple

L’exemple suivant génère C3446 dans Visual Studio 2017 et versions ultérieures :

```cpp
// C3446.cpp
value struct V
{
       int i = 0; // error C3446: 'V::i': a default member initializer
                  // is not allowed for a member of a value class
       int j {0}; // C3446
};
```

Pour corriger cette erreur, supprimez l’initialiseur :

```cpp
// C3446b.cpp
value struct V
{
       int i;
       int j;
};
```

