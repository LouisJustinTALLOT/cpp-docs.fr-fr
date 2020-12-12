---
description: 'En savoir plus sur : erreur du compilateur C3469'
title: Erreur du compilateur C3469
ms.date: 11/04/2016
f1_keywords:
- C3469
helpviewer_keywords:
- C3469
ms.assetid: e23b0e5c-c704-4e67-a868-bf02c2055d85
ms.openlocfilehash: 3a08cbc21405a78b6f624463c379d07860210b72
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113426"
---
# <a name="compiler-error-c3469"></a>Erreur du compilateur C3469

'type' : impossible de transférer une classe générique

Vous ne pouvez pas utiliser le transfert de type sur une classe générique.

Pour plus d’informations, consultez [transfert de type (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Exemples

L’exemple suivant crée un composant.

```cpp
// C3469.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

L’exemple suivant génère l’erreur C3466 :

```cpp
// C3469_b.cpp
// compile with: /clr /c
#using "C3469.dll"
[assembly:TypeForwardedTo(GR::typeid)];   // C3469
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```
