---
description: 'En savoir plus sur : erreur irrécupérable C1191'
title: Erreur irrécupérable C1191
ms.date: 11/04/2016
f1_keywords:
- C1191
helpviewer_keywords:
- C1191
ms.assetid: 2888c6c4-b4e6-449e-8ee0-7917f31086df
ms.openlocfilehash: ef7f9ec6554daf0d83f3e597877509025512a6d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123576"
---
# <a name="fatal-error-c1191"></a>Erreur irrécupérable C1191

'dll’ne peut être importé qu’au niveau de la portée globale

L’instruction permettant d’importer des mscorlib.dll dans un programme qui utilise la programmation/CLR ne peut pas apparaître dans un espace de noms ou une fonction, mais elle doit apparaître au niveau de la portée globale.

L’exemple suivant génère l’C1191 :

```cpp
// C1191.cpp
// compile with: /clr
namespace sample {
   #using <mscorlib.dll>   // C1191 not at global scope
}
```

Solution possible :

```cpp
// C1191b.cpp
// compile with: /clr /c
#using <mscorlib.dll>
namespace sample {}
```
