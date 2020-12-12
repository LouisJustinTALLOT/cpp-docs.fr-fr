---
description: 'En savoir plus sur : erreur du compilateur C2479'
title: Erreur du compilateur C2479
ms.date: 11/04/2016
f1_keywords:
- C2479
helpviewer_keywords:
- C2479
ms.assetid: c74c7869-e65b-4ca1-b6fa-eb39fed4458a
ms.openlocfilehash: 7193112ee546b7314075b105cb88c68fce71a256
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123940"
---
# <a name="compiler-error-c2479"></a>Erreur du compilateur C2479

'identifier' : 'Allocate () 'n’est valide que pour les éléments de données d’étendue statique

La `__declspec( allocate())` syntaxe peut être utilisée uniquement pour les données statiques.

L’exemple suivant génère l’C2479 :

```cpp
// C2479.cpp
// compile with: /c
#pragma section("mycode", read)
static __declspec(allocate("mycode")) void DoNothing() {}   // C2479
__declspec(allocate("mycode"))  int i = 0;   // OK
```
