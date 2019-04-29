---
title: Erreur du compilateur C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 8456e9b17b72cd4ac98349d2f2871a1c59f56911
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62311488"
---
# <a name="compiler-error-c3418"></a>Erreur du compilateur C3418

le spécificateur d’accès 'spécificateur' n’est pas pris en charge

Un spécificateur d’accès CLR a été spécifié de manière incorrecte.  Pour plus d’informations, consultez la visibilité du Type et la visibilité des membres dans [Comment : Définir et consommer des Classes et Structs (C++ / c++ / CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3418.

```cpp
// C3418.cpp
// compile with: /clr /c
ref struct m {
internal public:   // C3418
   void test(){}
};

ref struct n {
internal:   // OK
   void test(){}
};
```