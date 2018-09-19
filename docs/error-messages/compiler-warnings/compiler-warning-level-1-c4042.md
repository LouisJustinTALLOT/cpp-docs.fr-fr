---
title: Compilateur avertissement (niveau 1) C4042 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4042
dev_langs:
- C++
helpviewer_keywords:
- C4042
ms.assetid: e4bd861b-1194-426b-bf79-68c5b021eb0a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5bef2071cf31123b5b172df2651c0d6a6d87d4fc
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46067469"
---
# <a name="compiler-warning-level-1-c4042"></a>Compilateur avertissement (niveau 1) C4042

'identificateur' : classe de stockage incorrecte

La classe de stockage spécifié ne peut pas être utilisée avec cet identificateur dans ce contexte. Le compilateur utilise la classe de stockage par défaut à la place :

- `extern`, si *identificateur* est une fonction.

- **Auto**si *identificateur* est un paramètre formel ou une variable locale.

- Aucun stockage ne classe si *identificateur* est une variable globale.

Cet avertissement peut être dû à la spécification d’une classe de stockage autre que **inscrire** dans une déclaration de paramètre.

L’exemple suivant génère C4042

```
// C4042.cpp
// compile with: /W1 /LD
int func2( __declspec( thread ) int tls_i )    // C4042
// try the following line instead
// int func2( int tls_i )
{
   return tls_i;
}
```