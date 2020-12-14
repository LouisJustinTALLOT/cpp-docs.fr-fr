---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4624'
title: Avertissement du compilateur (niveau 1) C4624
ms.date: 11/04/2016
f1_keywords:
- C4624
helpviewer_keywords:
- C4624
ms.assetid: 14f61769-d92e-482b-9515-debd87b30a66
ms.openlocfilehash: d5869742b548c4a54efe08e686571123fc570517
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97281455"
---
# <a name="compiler-warning-level-1-c4624"></a>Avertissement du compilateur (niveau 1) C4624

'classe dérivée' : le destructeur a été défini de manière implicite comme supprimé car un destructeur de la classe de base est inaccessible ou supprimé

Un destructeur n'était pas accessible ou était supprimé dans une classe de base et n'a donc pas été généré pour une classe dérivée. Toute tentative pour créer un objet de ce type dans la pile provoquera une erreur du compilateur.

L'exemple suivant génère l'erreur C4624 et montre comment la corriger :

```cpp
// C4624.cpp
// compile with: /W1 /c
class B {
// Uncomment the following line to fix.
// public:
   ~B();
};

class D : public B {};   // C4624 B's destructor not public
```
