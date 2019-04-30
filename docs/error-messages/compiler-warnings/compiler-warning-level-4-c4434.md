---
title: Avertissement du compilateur (niveau 4) C4434
ms.date: 11/04/2016
f1_keywords:
- C4434
helpviewer_keywords:
- C4434
ms.assetid: 24b8785e-353a-4c37-8bed-ed61001a871d
ms.openlocfilehash: 6a7d760a7d192c7e0a7bd5e16f77efe1a4099c31
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62391489"
---
# <a name="compiler-warning-level-4-c4434"></a>Avertissement du compilateur (niveau 4) C4434

un constructeur de classe doit avoir un accès privé ; modification d’un accès privé

C4434 indique que le compilateur a modifié l’accessibilité d’un constructeur statique. Constructeurs statiques doivent avoir une accessibilité privée, comme ils sont uniquement destinés à être appelée par le common language runtime. Pour plus d’informations, consultez [constructeurs statiques](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md#BKMK_Static_constructors).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C4434.

```
// C4434.cpp
// compile with: /W4 /c /clr
public ref struct R {
   static R(){}   // C4434
};
```