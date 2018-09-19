---
title: Erreur du compilateur C2150 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2150
dev_langs:
- C++
helpviewer_keywords:
- C2150
ms.assetid: 21e82a10-c1d4-4c0d-9dc6-c5d92ea42a31
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ef0920c98fe59fe5bca49bba4c62a486a61c0a55
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46024708"
---
# <a name="compiler-error-c2150"></a>Erreur du compilateur C2150

> «*identificateur*' : champ de bits doit être de type 'int', 'signed int' ou 'unsigned int'

Le type de base pour un champ de bits doit être `int`, `signed int`, ou `unsigned int`.

## <a name="example"></a>Exemple

Cet exemple montre comment vous pouvez rencontrer C2150, et comment vous pouvez y remédier :

```cpp
// C2150.cpp
// compile with: /c
struct A {
   float a : 8;    // C2150
   int i : 8;      // OK
};
```