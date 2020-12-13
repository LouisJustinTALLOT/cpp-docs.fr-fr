---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4674'
title: Avertissement du compilateur (niveau 1) C4674
ms.date: 11/04/2016
f1_keywords:
- C4674
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
ms.openlocfilehash: 1df7dd982f52a6987e06e888130953c1a9deb330
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97334980"
---
# <a name="compiler-warning-level-1-c4674"></a>Avertissement du compilateur (niveau 1) C4674

'method' doit être déclaré 'static' et avoir un seul paramètre

La signature d’un opérateur de conversion n’était pas correcte. La méthode n’est pas considérée comme une conversion définie par l’utilisateur. Pour plus d’informations sur la définition des opérateurs, consultez [opérateurs définis par l’utilisateur (c++/CLI)](../../dotnet/user-defined-operators-cpp-cli.md) et [conversions définies par l’utilisateur (c++/CLI)](../../dotnet/user-defined-conversions-cpp-cli.md).

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
