---
description: 'En savoir plus sur : erreur du compilateur C3460'
title: Erreur du compilateur C3460
ms.date: 11/04/2016
f1_keywords:
- C3460
helpviewer_keywords:
- C3460
ms.assetid: adbf8775-10ca-4654-acdf-58dd765351cd
ms.openlocfilehash: ee5bcb2396586d965f16d80ef006301c7bcd784f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315879"
---
# <a name="compiler-error-c3460"></a>Erreur du compilateur C3460

'type' : seul un type défini par l’utilisateur peut être transféré

Pour plus d’informations, consultez [transfert de type (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Exemples

L’exemple suivant crée un composant.

```cpp
// C3460.cpp
// compile with: /LD /clr
public ref class R {};
```

L’exemple suivant génère l’erreur C3460.

```cpp
// C3460_b.cpp
// compile with: /clr /c
#using "C3460.dll"
[assembly:TypeForwardedTo(int::typeid)];   // C3460
[assembly:TypeForwardedTo(R::typeid)];
```
