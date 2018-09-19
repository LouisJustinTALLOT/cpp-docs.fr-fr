---
title: Compilateur avertissement (niveau 4) C4131 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C4131
dev_langs:
- C++
helpviewer_keywords:
- C4131
ms.assetid: 7903b3e1-454f-4be2-aa9b-230992f96a2d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 43de917b2a6aff38602a6118e599c0d9df262a70
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46033184"
---
# <a name="compiler-warning-level-4-c4131"></a>Avertissement du compilateur (niveau 4) C4131

'fonction' : utilise un déclarateur obsolète

La déclaration de fonction spécifiée n’est pas sous forme de prototype.

Les anciennes déclarations de fonction doivent être converties sous forme de prototypes.

L’exemple suivant montre une ancienne déclaration de fonction :

```
// C4131.c
// compile with: /W4 /c
void addrec( name, id ) // C4131 expected
char *name;
int id;
{ }
```

L’exemple suivant montre une forme de prototype :

```
void addrec( char *name, int id )
{ }
```