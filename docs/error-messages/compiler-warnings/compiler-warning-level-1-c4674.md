---
title: Compilateur avertissement (niveau 1) C4674 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4674
dev_langs:
- C++
helpviewer_keywords:
- C4674
ms.assetid: 638dae0b-b82c-4865-9599-72630827ca09
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 9b2f945982e80b49403387241f29a50876274e66
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024877"
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
