---
title: Erreur du compilateur C2801 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2801
dev_langs:
- C++
helpviewer_keywords:
- C2801
ms.assetid: 35dfc7ea-9e37-4e30-baa1-944dc61302f5
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d57ee5bf5f5152ef55852c9f9b829bc4a1d17d41
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46040633"
---
# <a name="compiler-error-c2801"></a>Erreur du compilateur C2801

'operator opérateur' doit être un membre non static

Les opérateurs suivants peuvent être surchargées uniquement en tant que membres non statiques :

- Affectation `=`

- Accès au membre de classe `->`

- Mettre en indice `[]`

- Appel de fonction `()`

Causes possibles de l’erreur C2801 :

- Opérateur surchargé n’est pas une classe, une structure ou un membre d’union.

- Opérateur surchargé est déclaré `static`.

- L’exemple suivant génère l’erreur C2801 :

```
// C2801.cpp
// compile with: /c
operator[]();   // C2801 not a member
class A {
   static operator->();   // C2801 static
   operator()();   // OK
};
```