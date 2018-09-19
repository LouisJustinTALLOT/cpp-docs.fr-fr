---
title: Erreur du compilateur C2165 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2165
dev_langs:
- C++
helpviewer_keywords:
- C2165
ms.assetid: b108313b-b8cb-4dce-b2ec-f2b31c9cdc87
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d0e9047b7f096c855bbefec745b454e2289c05e9
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46101109"
---
# <a name="compiler-error-c2165"></a>Erreur du compilateur C2165

'keyword' : impossible de modifier les pointeurs vers des données

Le mot clé `__stdcall`, `__cdecl`ou `__fastcall` tente de modifier un pointeur vers des données.

L’exemple suivant génère l’erreur C2165 :

```
// C2165.cpp
// compile with: /c
char __cdecl *p;   // C2165
char *p;   // OK
```