---
title: Compilateur avertissement (niveau 1) C4172 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4172
dev_langs:
- C++
helpviewer_keywords:
- C4172
ms.assetid: a8d2bf65-d8b1-4fe3-8340-a223d7e7fde6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 56f606b48fb060472dd67d34800c06946bc41712
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46043506"
---
# <a name="compiler-warning-level-1-c4172"></a>Compilateur avertissement (niveau 1) C4172

Retourne l’adresse de variable locale ou temporaire

Une fonction retourne l’adresse d’un objet temporaire ou de variable local. Variables locales et des objets temporaires sont détruits quand une fonction est retournée, l’adresse retournée n’est pas valide.

Remaniez la fonction afin qu’elle ne retourne pas l’adresse d’un objet local.

L’exemple suivant génère l’erreur C4172 :

```
// C4172.cpp
// compile with: /W1 /LD
float f = 10;

const double& bar() {
// try the following line instead
// const float& bar() {
   return f;   // C4172
}
```