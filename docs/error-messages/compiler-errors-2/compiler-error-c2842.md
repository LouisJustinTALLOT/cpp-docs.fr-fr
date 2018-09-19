---
title: Erreur du compilateur C2842 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2842
dev_langs:
- C++
helpviewer_keywords:
- C2842
ms.assetid: 8674f08d-9f50-46ad-9229-abc6b74fa0e5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 20967ab4cd047f62a5cf692c91fec90148b4f470
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118815"
---
# <a name="compiler-error-c2842"></a>Erreur du compilateur C2842

'classe' : un type managé ou WinRT ne peut pas définir son propre 'operator new' ou 'operator delete'

Vous pouvez définir vos propres ** opérateur new ou **opérateur delete** pour gérer l’allocation de mémoire sur le tas natif. Toutefois, les classes de référence ne peuvent pas définir ces opérateurs car ils sont alloués seulement sur le tas managé.


Pour plus d’informations, consultez [les opérateurs définis par l’utilisateur (C++ / c++ / CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Exemple

L'exemple suivant génère l'erreur C2842.

```
// C2842.cpp
// compile with: /clr /c
ref class G {
   void* operator new( size_t nSize );   // C2842
};
```
