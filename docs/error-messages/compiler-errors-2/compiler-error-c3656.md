---
description: 'En savoir plus sur : erreur du compilateur C3656'
title: Erreur du compilateur C3656
ms.date: 11/04/2016
f1_keywords:
- C3656
helpviewer_keywords:
- C3656
ms.assetid: 88965d85-73b0-4b35-8020-0650c9c94cd8
ms.openlocfilehash: ad87b989bf0e094a011ac5451745d5d296a0c223
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97134431"
---
# <a name="compiler-error-c3656"></a>Erreur du compilateur C3656

'override' : le spécificateur de substitution ne peut pas être répété

Un mot clé de substitution explicite ne peut être spécifié qu’une seule fois. Pour plus d’informations, consultez [substitutions explicites](../../extensions/explicit-overrides-cpp-component-extensions.md).

L’exemple suivant génère l’C3656 :

```cpp
// C3656.cpp
// compile with: /clr /c
public interface struct O {
   int f();
};

public ref struct V : O {
   int f() override override { return 0; }   // C3656
   // try the following line instead
   // int f() override { return 0; }
};
```
