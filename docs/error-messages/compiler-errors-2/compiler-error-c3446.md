---
title: Erreur du compilateur C3446
ms.date: 07/21/2017
f1_keywords:
- C3446
helpviewer_keywords:
- C3446
ms.assetid: 33064548-24e4-46f1-beb1-476e3c3b3fbf
ms.openlocfilehash: 0f9ebd274a90dffe00b0e8375cc374acf46e7a08
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79447123"
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

