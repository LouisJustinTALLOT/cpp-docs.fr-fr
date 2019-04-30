---
title: Erreur du compilateur C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: dcfac9629a90b82744f87ec105c30301b2102cdf
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62408743"
---
# <a name="compiler-error-c2062"></a>Erreur du compilateur C2062

type 'type' inattendu

Le compilateur ne vous attendiez pas un nom de type.

L’exemple suivant génère l’erreur C2062 :

```
// C2062.cpp
// compile with: /c
struct A {  : int l; };   // C2062
struct B { private: int l; };   // OK
```

L’erreur C2062 peut également se produire en raison de la manière dont le compilateur gère les types dans la liste des paramètres d’un constructeur non défini. Si le compilateur rencontre un type indéfini (mal orthographié ?), il suppose que le constructeur est une expression et émet l’erreur C2062. Pour résoudre, utilisez uniquement des types définis dans une liste de paramètres de constructeur.