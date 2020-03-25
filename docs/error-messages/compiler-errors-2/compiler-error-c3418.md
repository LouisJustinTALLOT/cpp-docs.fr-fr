---
title: Erreur du compilateur C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 21023bfb551a1894e25cc4940892dde0f0440a0e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80200877"
---
# <a name="compiler-error-c3418"></a>Erreur du compilateur C3418

le spécificateur d’accès 'spécificateur' n’est pas pris en charge

Un spécificateur d’accès CLR a été spécifié de manière incorrecte.  Pour plus d’informations, consultez visibilité des types et visibilité des membres dans Guide pratique [pour définir et consommer des classesC++et des structs (/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

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
