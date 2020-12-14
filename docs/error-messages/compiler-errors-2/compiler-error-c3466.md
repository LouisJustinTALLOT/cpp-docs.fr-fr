---
description: 'En savoir plus sur : erreur du compilateur C3466'
title: Erreur du compilateur C3466
ms.date: 11/04/2016
f1_keywords:
- C3466
helpviewer_keywords:
- C3466
ms.assetid: 69a877d9-a749-474b-bfc3-8d3fd53ba8fd
ms.openlocfilehash: 53280a5295676fb6b5cee1d25f5fc96f5b906ebc
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97315710"
---
# <a name="compiler-error-c3466"></a>Erreur du compilateur C3466

'type' : une spécialisation d’une classe générique ne peut pas être transférée

Vous ne pouvez pas utiliser le transfert de type sur une spécialisation d’une classe générique.

Pour plus d’informations, consultez [transfert de type (C++/CLI)](../../extensions/type-forwarding-cpp-cli.md).

## <a name="examples"></a>Exemples

L’exemple suivant crée un composant.

```cpp
// C3466.cpp
// compile with: /clr /LD
generic<typename T>
public ref class GR {};

public ref class GR2 {};
```

L’exemple suivant génère l’erreur C3466 :

```cpp
// C3466_b.cpp
// compile with: /clr /c
#using "C3466.dll"
[assembly:TypeForwardedTo(GR<int>::typeid)];   // C3466
[assembly:TypeForwardedTo(GR2::typeid)];   // OK
```
