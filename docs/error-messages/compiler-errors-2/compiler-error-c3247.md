---
description: 'En savoir plus sur : erreur du compilateur C3247'
title: Erreur du compilateur C3247
ms.date: 11/04/2016
f1_keywords:
- C3247
helpviewer_keywords:
- C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
ms.openlocfilehash: 02e8f20f9804067e0179f3b5583d589d16dae302
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97307181"
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
