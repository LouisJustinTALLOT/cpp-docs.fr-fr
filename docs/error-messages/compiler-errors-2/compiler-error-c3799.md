---
title: Erreur du compilateur C3799 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3799
dev_langs:
- C++
helpviewer_keywords:
- C3799
ms.assetid: 336a2811-9370-4e6e-b03b-325bda470805
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1022a2a1f5c5bb6279fc4af0acedbf28d7723aa6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46105265"
---
# <a name="compiler-error-c3799"></a>Erreur du compilateur C3799

propriété indexée ne peut pas avoir une liste de paramètres vide

Une propriété indexée a été correctement déclarée. Pour plus d’informations, consultez [Comment : utilisez les propriétés en C / c++ / CLI](../../dotnet/how-to-use-properties-in-cpp-cli.md).

## <a name="example"></a>Exemple

L’exemple suivant génère C3799 et montre comment la corriger.

```cpp
// C3799.cpp
// compile with: /clr /c
ref struct C {
   property int default[] {   // C3799
   // try the following line instead
   // property int default[int] {
      int get(int index) { return 0; }
      void set(int index, int value) {}
   }
};
```