---
title: Avertissement du compilateur (niveau 1) C4684
ms.date: 11/04/2016
f1_keywords:
- C4684
helpviewer_keywords:
- C4684
ms.assetid: e95f1a83-2784-4b05-ae94-12148e056e26
ms.openlocfilehash: 8ba3d75ecb370ac86c9a6ab47f05dd49fc12ba23
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50479116"
---
# <a name="compiler-warning-level-1-c4684"></a>Avertissement du compilateur (niveau 1) C4684

'attribute' : avertissement !! attribut peut entraîner une génération de code non valide : utilisez avec précaution

Vous avez utilisé un attribut qui ne doit pas couramment utilisé.

L’exemple suivant génère l’erreur C4684 :

```
// C4684.cpp
// compile with: /W1 /LD
[module(name="xx")]; // C4684 expected
[no_injected_text];
```