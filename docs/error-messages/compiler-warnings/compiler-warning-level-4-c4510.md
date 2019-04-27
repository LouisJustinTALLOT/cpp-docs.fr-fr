---
title: Avertissement du compilateur (niveau 4) C4510
ms.date: 11/04/2016
f1_keywords:
- C4510
helpviewer_keywords:
- C4510
ms.assetid: fd28d1d4-ad27-4dad-94c0-9dba46c93180
ms.openlocfilehash: 80183e9f7ef17cbc37592f36eb8db1df2be94827
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62221087"
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