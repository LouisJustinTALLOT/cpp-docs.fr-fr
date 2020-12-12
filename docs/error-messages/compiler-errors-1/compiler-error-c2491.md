---
description: 'En savoir plus sur : erreur du compilateur C2491'
title: Erreur du compilateur C2491
ms.date: 11/04/2016
f1_keywords:
- C2491
helpviewer_keywords:
- C2491
ms.assetid: 4e5a8f81-124e-402c-a5ec-d35a89b5469e
ms.openlocfilehash: 4fd12e30672d7045aa4a7506b35b845e8cd018c9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97283701"
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
