---
title: Erreur du compilateur C2906
ms.date: 11/04/2016
f1_keywords:
- C2906
helpviewer_keywords:
- C2906
ms.assetid: 30f652f1-6af6-4a2f-a69e-a1a4876cc8c6
ms.openlocfilehash: 621b31cf362c1dcc740390cf9e405b7da3f05da8
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50587770"
---
# <a name="compiler-error-c2906"></a>Erreur du compilateur C2906

'specialization' : une spécialisation explicite requiert 'modèle <>'

Vous devez utiliser la nouvelle syntaxe pour la spécialisation explicite de modèles.

L’exemple suivant génère l’erreur C2906 :

```
// C2906.cpp
// compile with: /c
template<class T> class X{};   // primary template
class X<int> { }   // C2906
template<> class X<int> { };   // new syntax
```