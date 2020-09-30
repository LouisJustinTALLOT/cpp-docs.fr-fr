---
title: Erreur du compilateur C3734
ms.date: 11/04/2016
f1_keywords:
- C3734
helpviewer_keywords:
- C3734
ms.assetid: 4e2afdcc-7da9-45a1-9c96-85f25e2986e8
ms.openlocfilehash: 0d49eae823eb64f97e7276d432e161b3de21d725
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91510076"
---
# <a name="compiler-error-c3734"></a>Erreur du compilateur C3734

'classe' : une classe managée ou WinRT ne peut pas être une coclasse

L’attribut [coclass](../../windows/attributes/coclass.md) ne peut pas être utilisé avec des classes managées ou WinRT.

L'exemple suivant génère l'erreur C3734 et montre comment la corriger :

```cpp
// C3734.cpp
// compile with: /clr /c
[module(name="x")];

[coclass]
ref class CMyClass {   // C3734 remove the ref keyword to resolve
};
```
