---
title: Erreur du compilateur C2062 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2062
dev_langs:
- C++
helpviewer_keywords:
- C2062
ms.assetid: 6cc98353-2ddf-43ab-88a2-9cc91cdd6033
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: bbda0894b25e09681207d6447bb40727d490fc02
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46072242"
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