---
title: Erreur du compilateur C3622 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3622
dev_langs:
- C++
helpviewer_keywords:
- C3622
ms.assetid: 02836f78-0cf2-4947-b87e-710187d81014
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 13ba39a2baf9da2039bbc97fe459f8840effacea
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062408"
---
# <a name="compiler-error-c3622"></a>Erreur du compilateur C3622

'classe' : une classe déclarée comme 'mot_clé' ne peut pas être instanciée.

Une tentative a été faite pour instancier une classe marquée en tant que [abstraite](../../windows/abstract-cpp-component-extensions.md). Une classe marquée en tant que `abstract` peut être une classe de base, mais elle ne peut pas être instanciée.

## <a name="example"></a>Exemple

L’exemple suivant génère C3622.

```
// C3622.cpp
// compile with: /clr
ref class a abstract {};

int main() {
   a aa;   // C3622
}
```
