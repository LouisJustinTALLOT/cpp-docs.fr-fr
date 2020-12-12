---
description: 'En savoir plus sur : erreur du compilateur C2600'
title: Erreur du compilateur C2600
ms.date: 11/04/2016
f1_keywords:
- C2600
helpviewer_keywords:
- C2600
ms.assetid: cce11943-ea01-4bee-a7b0-b67d24ec6493
ms.openlocfilehash: fbd99cb50bc3afc748e1d3b2e954c584a7cef78b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97120020"
---
# <a name="compiler-error-c2600"></a>Erreur du compilateur C2600

'fonction' : impossible de définir une fonction membre spéciale générée par le compilateur (doit être déclarée d'abord dans la classe)

Pour que les fonctions membres telles que les constructeurs ou les destructeurs puissent être définies pour une classe, elles doivent être déclarées dans la classe. Le compilateur peut générer des constructeurs et des destructeurs par défaut (appelés fonctions membres spéciales) si aucun n'est déclaré dans la classe. Cependant, si vous définissez une de ces fonctions sans déclaration correspondante dans la classe, le compilateur détecte un conflit.

Pour corriger cette erreur, dans la déclaration de la classe, déclarez chaque fonction membre que vous définissez en dehors de la déclaration de la classe.

L'exemple suivant génère l'erreur C2600 :

```cpp
// C2600.cpp
// compile with: /c
class C {};
C::~C() {}   // C2600

class D {
   D::~D();
};

D::~D() {}
```
