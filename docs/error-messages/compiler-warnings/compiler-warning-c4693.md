---
title: Avertissement du compilateur C4693 | Documents Microsoft
ms.date: 10/25/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4693
dev_langs:
- C++
helpviewer_keywords:
- C4693
ms.assetid: 72d8db01-5e6f-4794-8731-76107e8f064a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f8230e60d65c80b4f839cc8a1c97ccc0c7b18086
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33273879"
---
# <a name="compiler-warning-c4693"></a>Avertissement du compilateur C4693

> 'classe' : une classe abstraite sealed ne peut pas avoir de membres d’instance 'test'

Si un type est marqué [sealed](../../windows/sealed-cpp-component-extensions.md) et [abstraite](../../windows/abstract-cpp-component-extensions.md), il ne peut comporter que des membres statiques.

Cet avertissement est automatiquement promu en une erreur. Si vous souhaitez modifier ce comportement, utilisez [#pragma warning](../../preprocessor/warning.md).

## <a name="example"></a>Exemple

L’exemple suivant génère l’avertissement C4693.

```cpp
// C4693.cpp
// compile with: /clr /c
public ref class Public_Ref_Class sealed abstract {
public:
   void Test() {}   // C4693
   static void Test2() {}   // OK
};
```