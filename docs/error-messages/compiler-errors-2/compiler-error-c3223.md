---
description: 'En savoir plus sur : erreur du compilateur C3223'
title: Erreur du compilateur C3223
ms.date: 11/04/2016
f1_keywords:
- C3223
helpviewer_keywords:
- C3223
ms.assetid: 1f4380b4-0413-40db-a868-62f97babaf78
ms.openlocfilehash: d768bba53634e3614ba4dc583cb57d2d16e744fa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97267688"
---
# <a name="compiler-error-c3223"></a>Erreur du compilateur C3223

'property' : 'typeid' ne peut pas être appliqué à une propriété

[typeid](../../extensions/typeid-cpp-component-extensions.md) ne peut pas être appliqué à une propriété.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3223 :

```cpp
// C3223.cpp
// compile with: /clr
ref class R {
public:
   property int myprop;
};

int main() {
   System::Type^ type2 = R::myprop::typeid;   // C3223
}
```
