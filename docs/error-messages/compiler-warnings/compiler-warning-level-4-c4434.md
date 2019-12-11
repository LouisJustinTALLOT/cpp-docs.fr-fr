---
title: Avertissement du compilateur (niveau 4) C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: fccc37ec531768adbe332ddf9fd91ceb708c7185
ms.sourcegitcommit: 573b36b52b0de7be5cae309d45b68ac7ecf9a6d8
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/10/2019
ms.locfileid: "74990816"
---
# <a name="compiler-warning-level-4-c4434"></a>Avertissement du compilateur (niveau 4) C4434

un constructeur de classe doit avoir un accès privé ; passage à l’accès privé

C4434 indique que le compilateur a modifié l’accessibilité d’un constructeur statique. Les constructeurs statiques doivent avoir une accessibilité privée, car ils sont uniquement destinés à être appelés par le common language runtime. Pour plus d’informations, consultez [constructeurs statiques](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C4434.

```cpp
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```
