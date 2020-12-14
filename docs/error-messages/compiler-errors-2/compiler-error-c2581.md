---
description: 'En savoir plus sur : erreur du compilateur C2581'
title: Erreur du compilateur C2581
ms.date: 11/04/2016
f1_keywords:
- C2581
helpviewer_keywords:
- C2581
ms.assetid: 24a4e4c1-24d3-4e42-b760-7dcaf9740b16
ms.openlocfilehash: 9de6c48c2ade71af238cc62a0f92e642e1262d3b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97282118"
---
# <a name="compiler-error-c2581"></a>Erreur du compilateur C2581

'type' : fonction static’operator = 'non conforme

L’opérateur d’assignation ( `=` ) est déclaré de manière incorrecte comme **`static`** . Les opérateurs d’assignation ne peuvent pas être **`static`** . Pour plus d’informations, consultez [opérateurs définis par l’utilisateur (C++/CLI)](../../dotnet/user-defined-operators-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’C2581.

```cpp
// C2581.cpp
// compile with: /clr /c
ref struct Y {
   static Y ^ operator = (Y^ me, int i);   // C2581
   Y^ operator =(int i);   // OK
};
```
