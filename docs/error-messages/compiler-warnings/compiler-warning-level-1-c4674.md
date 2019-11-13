---
title: Avertissement du compilateur (niveau 1) C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: b9428a593ff59cbdfa6d8eb369413a560b4a5ad2
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74052546"
---
# <a name="compiler-warning-level-1-c4674"></a>Avertissement du compilateur (niveau 1) C4674

'method' doit être déclaré 'static' et avoir un seul paramètre

La signature d’un opérateur de conversion n’était pas correcte. La méthode n’est pas considérée comme une conversion définie par l’utilisateur. Pour plus d’informations sur la définition des opérateurs, consultez [opérateurs définisC++par l’utilisateur (/CLI)](../../dotnet/user-defined-operators-cpp-cli.md) et [conversionsC++définies par l’utilisateur (/CLI)](../../dotnet/user-defined-conversions-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4674.

```cpp
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```
