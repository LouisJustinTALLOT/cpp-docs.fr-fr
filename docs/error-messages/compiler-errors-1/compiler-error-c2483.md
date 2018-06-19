---
title: Erreur du compilateur C2483 | Documents Microsoft
ms.custom: ''
ms.date: 09/15/2017
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2483
dev_langs:
- C++
helpviewer_keywords:
- C2483
ms.assetid: 5762b325-914b-442d-a604-e4617ba04038
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0a10fd33ebeef43904db964fc327fb749029f963
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33197973"
---
# <a name="compiler-error-c2483"></a>Erreur du compilateur C2483

>'*identificateur*' : l’objet avec constructeur ou destructeur ne peut pas être déclaré comme 'thread'

Ce message d’erreur est obsolète dans Visual Studio 2015 et versions ultérieures. Dans les versions précédentes, les variables déclarées avec le `thread` attribut ne peut pas être initialisé avec un constructeur ou une autre expression qui requiert une évaluation de l’exécution. Une expression statique est requise pour initialiser `thread` données.

## <a name="example"></a>Exemple

L’exemple suivant génère C2483 dans Visual Studio 2013 et versions antérieures.

```cpp
// C2483.cpp
// compile with: /c
__declspec(thread) struct A {
   A(){}
   ~A(){}
} aa;   // C2483 error  

__declspec(thread) struct B {} b;   // OK
```

## <a name="see-also"></a>Voir aussi

[thread](../../cpp/thread.md)