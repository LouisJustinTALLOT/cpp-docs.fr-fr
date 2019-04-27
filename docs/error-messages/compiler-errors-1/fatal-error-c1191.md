---
title: Erreur irrécupérable C1191
ms.date: 11/04/2016
f1_keywords:
- C1191
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
ms.openlocfilehash: 89af73699120ee4d8af3cda746727d758ef6d22c
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228878"
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