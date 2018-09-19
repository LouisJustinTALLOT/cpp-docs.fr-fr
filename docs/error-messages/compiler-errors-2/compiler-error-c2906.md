---
title: Erreur du compilateur C2906 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2906
dev_langs:
- C++
helpviewer_keywords:
- C2906
ms.assetid: 30f652f1-6af6-4a2f-a69e-a1a4876cc8c6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 608109d6a040345610a47ac2e43a51a813a3c6bf
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46059032"
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