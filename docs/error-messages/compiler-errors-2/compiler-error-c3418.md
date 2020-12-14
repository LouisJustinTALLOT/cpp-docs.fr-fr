---
description: 'En savoir plus sur : erreur du compilateur C3418'
title: Erreur du compilateur C3418
ms.date: 11/04/2016
f1_keywords:
- C3418
helpviewer_keywords:
- C3418
ms.assetid: 54042c04-3c45-41c1-bad7-90f9ee05a21b
ms.openlocfilehash: 38082b7fe9ffa0ebcc7b4857e77395664a9f0c42
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316230"
---
# <a name="compiler-error-c3418"></a>Erreur du compilateur C3418

le spécificateur d’accès 'spécificateur' n’est pas pris en charge

Un spécificateur d’accès CLR a été spécifié de manière incorrecte.  Pour plus d’informations, consultez visibilité des types et visibilité des membres dans Guide pratique [pour définir et consommer des classes et des structs (C++/CLI)](../../dotnet/how-to-define-and-consume-classes-and-structs-cpp-cli.md).

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
