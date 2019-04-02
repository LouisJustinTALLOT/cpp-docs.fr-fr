---
title: Erreur du compilateur C3223
ms.date: 11/04/2016
f1_keywords:
- C3223
helpviewer_keywords:
- C3223
ms.assetid: 1f4380b4-0413-40db-a868-62f97babaf78
ms.openlocfilehash: 5771de24cd07978903a3e598f1ff5658cb61eafa
ms.sourcegitcommit: 5cecccba0a96c1b4ccea1f7a1cfd91f259cc5bde
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/01/2019
ms.locfileid: "58776854"
---
# <a name="compiler-error-c3223"></a>Erreur du compilateur C3223

'property' : 'typeid' ne peut pas être appliqué à une propriété

[typeid](../../extensions/typeid-cpp-component-extensions.md) ne peut pas être appliqué à une propriété.

## <a name="example"></a>Exemple

L’exemple suivant génère l’erreur C3223 :

```
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