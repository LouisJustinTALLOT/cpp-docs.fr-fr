---
title: Avertissement du compilateur (niveau 1) C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: f7db2f37224a8defffb545b0cfaf018fd4654227
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62374545"
---
# <a name="compiler-warning-level-1-c4674"></a>Avertissement du compilateur (niveau 1) C4674

'method' doit être déclaré 'static' et avoir un seul paramètre

La signature d’un opérateur de conversion n’était pas correcte. La méthode n’est pas considérée comme une conversion définie par l’utilisateur. Pour plus d’informations sur la définition des opérateurs, consultez [les opérateurs définis par l’utilisateur (C++ / c++ / CLI)](../../dotnet/user-defined-operators-cpp-cli.md) et [les Conversions définies par l’utilisateur (C++ / c++ / CLI)](../../dotnet/user-defined-conversions-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4674.

```
// C4674.cpp
// compile with: /clr /WX /W1 /LD
ref class G {
   int op_Implicit(int i) {   // C4674
      return 0;
   }
};
```
