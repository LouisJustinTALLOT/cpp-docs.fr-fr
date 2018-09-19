---
title: Compilateur avertissement (niveau 1) C4615 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4615
dev_langs:
- C++
helpviewer_keywords:
- C4615
ms.assetid: 7b107c01-0da2-4e01-8b40-93813e30b94c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: cd260e37fb3f98f3e23d1c99c9ff53cae4f0198f
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46073698"
---
# <a name="compiler-warning-level-1-c4615"></a>Avertissement du compilateur (niveau 1) C4615

\#Avertissement de pragma : type d’avertissement utilisateur inconnu

Un spécificateur d’avertissement non valide a été utilisé avec **pragma** [avertissement](../../preprocessor/warning.md). Pour résoudre l’erreur, utilisez un spécificateur d’avertissement valide.

L’exemple suivant génère C4615 :

```
// C4615.cpp
// compile with: /W1 /LD
#pragma warning(enable : 4401)   // C4615, 'enable' not valid specifier

// use the code below to resolve the error
// #pragma warning(default : 4401)
```