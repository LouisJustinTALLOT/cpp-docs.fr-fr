---
title: Erreur du compilateur C3895
ms.date: 11/04/2016
f1_keywords:
- C3895
helpviewer_keywords:
- C3895
ms.assetid: 771b9fe5-d6d4-4297-bf57-e2f857722155
ms.openlocfilehash: 61dd280caa3c8c9b28dd77ecab2ed50ab9532d4b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50501282"
---
# <a name="compiler-error-c3895"></a>Erreur du compilateur C3895

'var' : les membres de données de type ne peut pas être 'volatiles'

Certains types des membres de données, par exemple [littéral](../../windows/literal-cpp-component-extensions.md) ou [initonly](../../dotnet/initonly-cpp-cli.md), ne peut pas être [volatile](../../cpp/volatile-cpp.md).

L’exemple suivant génère l’erreur C3895 :

```
// C3895.cpp
// compile with: /clr
ref struct Y1 {
   initonly
   volatile int data_var2;   // C3895
};
```