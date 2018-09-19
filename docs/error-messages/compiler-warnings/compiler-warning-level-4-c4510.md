---
title: Compilateur avertissement (niveau 4) C4510 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4510
dev_langs:
- C++
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: f2aaf7286c2e900629a18d7df5824ef4b7af1f5f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46048966"
---
# <a name="compiler-warning-level-4-c4510"></a>Avertissement du compilateur (niveau 4) C4510

'class' : constructeur par défaut n’a pas pu être généré.

Le compilateur ne peut pas générer un constructeur par défaut pour la classe spécifiée et aucun constructeur défini par l’utilisateur a été créé. Vous ne serez pas en mesure de créer des objets de ce type.

Il existe plusieurs situations qui empêchent le compilateur de générer un constructeur par défaut, y compris :

- Données membres const.

- Un membre de données qui est une référence.

Vous devez créer un constructeur par défaut défini par l’utilisateur pour la classe qui initialise ces membres.

L’exemple suivant génère l’erreur C4510 :

```
// C4510.cpp
// compile with: /W4
struct A {
   const int i;
   int &j;
   A& operator=( const A& ); // C4510 expected
   // uncomment the following line to resolve this C4510
   // A(int ii, int &jj) : i(ii), j(jj) {}
};   // C4510

int main() {
}
```