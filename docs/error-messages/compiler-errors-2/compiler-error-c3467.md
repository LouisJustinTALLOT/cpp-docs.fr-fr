---
description: 'En savoir plus sur : erreur du compilateur C3467'
title: Erreur du compilateur C3467
ms.date: 11/04/2016
f1_keywords:
- C3467
helpviewer_keywords:
- C3467
ms.assetid: e2b844d0-4920-412f-99fd-cd8051c4aa41
ms.openlocfilehash: c00c78852380537d744c8d01681a921e487826df
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97113439"
---
# <a name="compiler-error-c3467"></a>Erreur du compilateur C3467

'type' : ce type a déjà été transféré

Le compilateur a détecté plusieurs déclarations de type de transfert pour un même type. Seule une déclaration est autorisée par type.

Pour plus d’informations, consultez [transfert de type (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Exemples

L’exemple suivant crée un composant.

```cpp
// C3467.cpp
// compile with: /LD /clr
public ref class R {};
```

L’exemple suivant génère l’erreur C3467 :

```cpp
// C3467_b.cpp
// compile with: /clr /c
#using "C3467.dll"
[ assembly:TypeForwardedTo(R::typeid) ];
[ assembly:TypeForwardedTo(R::typeid) ];   // C3467
```
