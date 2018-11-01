---
title: Erreur du compilateur C2518
ms.date: 11/04/2016
f1_keywords:
- C2518
helpviewer_keywords:
- C2518
ms.assetid: a7895b47-da90-4851-ac97-18e81479595a
ms.openlocfilehash: d0a1f7bdc493a16b38dc2348097cc6cbea7ed898
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50657204"
---
# <a name="compiler-error-c2518"></a>Erreur du compilateur C2518

mot clé 'mot_clé' non conforme dans une liste de classe de base ; ignoré

Les mots clés `class` et `struct` ne doit pas apparaître dans une liste de classe de base.

L’exemple suivant génère l’erreur C2518 :

```
// C2518.cpp
// compile with: /c
class B {};
class C : public class B {};   // C2518
class D: public B {};   // OK
```