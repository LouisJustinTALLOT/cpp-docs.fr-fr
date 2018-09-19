---
title: Erreur du compilateur C2736 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2736
dev_langs:
- C++
helpviewer_keywords:
- C2736
ms.assetid: 95a6bc28-c0cb-49dc-87e6-e993dbbba881
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bda520c403de38481c5b84904aac5e733a90237c
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46049941"
---
# <a name="compiler-error-c2736"></a>Erreur du compilateur C2736

mot clé 'mot_clé' n’est pas autorisé dans un cast

Le mot clé n’est pas valide dans un cast.

L’exemple suivant génère l’erreur C2736 :

```
// C2736.cpp
int main() {
   return (virtual) 0;   // C2736
   // try the following line instead
   // return 0;
}
```