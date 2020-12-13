---
description: 'En savoir plus sur : erreur du compilateur C2062'
title: Erreur du compilateur C2062
ms.date: 11/04/2016
f1_keywords:
- C2062
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
ms.openlocfilehash: ef477fba9bb1208076dd6969cb78b7495d5536e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97328645"
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
