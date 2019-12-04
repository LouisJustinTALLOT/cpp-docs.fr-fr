---
title: Erreur du compilateur C2491
ms.date: 11/04/2016
f1_keywords:
- C2491
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
ms.openlocfilehash: 7ee7fb6e66ca9d5e09ad0eb445262c5f87d2060e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74757070"
---
# <a name="compiler-error-c2491"></a>Erreur du compilateur C2491

'identificateur' : définition de la fonction dllimport non autorisée

Données, données membres static et fonctions peuvent être déclarées comme `dllimport` mais pas définies comme `dllimport`.

Pour résoudre ce problème, supprimez le spécificateur `__declspec(dllimport)` de la définition de la fonction.

L'exemple suivant génère l'erreur C2491 :

```cpp
// C2491.cpp
// compile with: /c
// function definition
void __declspec(dllimport) funcB() {}   // C2491

// function declaration
void __declspec(dllimport) funcB();   // OK
```
