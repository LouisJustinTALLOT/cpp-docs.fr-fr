---
title: Erreur du compilateur C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: a709a540b24756a7e08f98552c5888a55c3ea601
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74735968"
---
# <a name="compiler-error-c2062"></a>Erreur du compilateur C2062

type’type’inattendu

Le compilateur n’attendait pas de nom de type.

L’exemple suivant génère l’C2062 :

```cpp
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

C2062 peut également se produire en raison de la façon dont le compilateur gère les types non définis dans la liste de paramètres d’un constructeur. Si le compilateur rencontre un type non défini (mal orthographié ?), il suppose que le constructeur est une expression et émet C2062. Pour résoudre le, utilisez uniquement des types définis dans une liste de paramètres de constructeur.
