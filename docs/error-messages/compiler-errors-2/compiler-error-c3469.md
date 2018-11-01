---
title: Erreur du compilateur C3469
ms.date: 11/04/2016
f1_keywords:
- C3469
helpviewer_keywords:
- C3469
ms.assetid: e23b0e5c-c704-4e67-a868-bf02c2055d85
ms.openlocfilehash: 7ae0b7b779749a9787601a6046eadd80c2ba49d0
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50571065"
---
# <a name="compiler-error-c3469"></a>Erreur du compilateur C3469

'type' : impossible de transférer une classe générique

Vous ne pouvez pas utiliser le transfert de type sur une classe générique.

Pour plus d’informations, consultez [transfert de Type (C++ / c++ / CLI)](../../windows/type-forwarding-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant crée un composant.

```
// C3469.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3466 :

```
// C3469_b.cpp
// compile with: /clr /c
#using "C3469.dll"
[assembly:TypeForwardedTo(GR::typeid)];   // C3469
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```