---
title: Erreur irrécupérable C1191 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C1191
dev_langs:
- C++
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: daefec7c89fc98d056963c4f761b7298d6e491cc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062967"
---
# <a name="fatal-error-c1191"></a>Erreur irrécupérable C1191

'dll' peut uniquement être importé dans une portée globale

L’instruction d’importation de mscorlib.dll dans un programme qui utilise la programmation /clr ne peut pas apparaître dans un espace de noms ou une fonction, mais il doit apparaître dans une portée globale.

L’exemple suivant génère l’erreur C1191 :

```
// C1191.cpp
// compile with: /clr
namespace sample {
   #using <mscorlib.dll>   // C1191 not at global scope
}
```

Solution possible :

```
// C1191b.cpp
// compile with: /clr /c
#using <mscorlib.dll>
namespace sample {}
```