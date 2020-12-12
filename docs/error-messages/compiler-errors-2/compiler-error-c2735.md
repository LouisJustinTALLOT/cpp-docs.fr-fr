---
description: 'En savoir plus sur : erreur du compilateur C2735'
title: Erreur du compilateur C2735
ms.date: 11/04/2016
f1_keywords:
- C2735
helpviewer_keywords:
- C2735
ms.assetid: 6ce45600-7148-4bc0-8699-af0ef137571e
ms.openlocfilehash: 75596e403c118d17ee286a579a347f6793c30bbd
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123147"
---
# <a name="compiler-error-c2735"></a>Erreur du compilateur C2735

le mot clé’keyword’n’est pas autorisé dans le spécificateur de type de paramètre formel

Le mot clé n’est pas valide dans ce contexte.

L’exemple suivant génère l’C2735 :

```cpp
// C2735.cpp
void f(inline int){}   // C2735
```
