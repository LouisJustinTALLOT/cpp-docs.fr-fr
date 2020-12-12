---
description: 'En savoir plus sur : erreur du compilateur C2199'
title: Erreur du compilateur C2199
ms.date: 11/04/2016
f1_keywords:
- C2199
helpviewer_keywords:
- C2199
ms.assetid: 6a92a1b7-7906-49e6-a31f-e8bffbc7706a
ms.openlocfilehash: e3c1daefb8a8b14c49b42e48c0d46d5a8e638953
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97278417"
---
# <a name="compiler-error-c2199"></a>Erreur du compilateur C2199

erreur de syntaxe : 'identifier (') trouvé au niveau de la portée globale (une déclaration était-elle prévue ?)

Le contexte spécifié a provoqué une erreur de syntaxe. Il se peut qu’il y ait une syntaxe de déclaration incorrecte.

L’exemple suivant génère l’C2199 :

```cpp
// C2199.cpp
// compile with: /c
int j = int(1) int(1);   // C2199
int j = 1;   // OK
```
