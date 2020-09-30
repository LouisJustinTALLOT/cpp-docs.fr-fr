---
title: Erreur du compilateur C3247
ms.date: 11/04/2016
f1_keywords:
- C3247
helpviewer_keywords:
- C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
ms.openlocfilehash: c1b8aaddac32af4e0936ce7d45fbc59c3835dda2
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91501379"
---
# <a name="compiler-error-c3247"></a>Erreur du compilateur C3247

'classe1' : une coclasse ne peut pas hériter d’une autre coclasse 'classe2'

Une classe marquée avec l’attribut [coclass](../../windows/attributes/coclass.md) ne peut pas hériter d’une classe marquée avec l’attribut `coclass` .

L’exemple suivant génère l’erreur C3247 :

```cpp
// C3247.cpp
[module(name="MyLib")];
[coclass]
class a {
};

[coclass]
class b : public a {   // C3247
};
int main() {
}
```
