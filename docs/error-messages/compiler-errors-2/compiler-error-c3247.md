---
title: Erreur du compilateur C3247 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3247
dev_langs:
- C++
helpviewer_keywords:
- C3247
ms.assetid: f9a2bbb5-3fce-40bf-9fd3-835a5f164dbb
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f706b4f1a1935a5c6246ea285c7e8b2b746f08cb
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46047237"
---
# <a name="compiler-error-c3247"></a>Erreur du compilateur C3247

'classe1' : une coclasse ne peut pas hériter d’une autre coclasse 'classe2'

Une classe marquée avec l’attribut [coclass](../../windows/coclass.md) ne peut pas hériter d’une classe marquée avec l’attribut `coclass` .

L’exemple suivant génère l’erreur C3247 :

```
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