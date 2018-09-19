---
title: Erreur du compilateur C3161 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3161
dev_langs:
- C++
helpviewer_keywords:
- C3161
ms.assetid: 1fe2be85-a343-487b-8476-bf9e257eb29d
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 11396ccad33489b41d18759ba4d2f00b445e94a3
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46136073"
---
# <a name="compiler-error-c3161"></a>Erreur du compilateur C3161

'interface' : classe d’imbrication, struct, union ou interface dans une interface n’est pas conforme ; imbrication d’une interface dans une classe, struct ou une union n’est pas conforme

Un [__interface](../../cpp/interface.md) peut uniquement apparaître dans une portée globale ou au sein d’un espace de noms. Une classe, un struct ou une union ne peut pas apparaître dans une interface.

## <a name="example"></a>Exemple

L’exemple suivant génère C3161.

```
// C3161.cpp
// compile with: /c
__interface X {
   __interface Y {};   // C3161 A nested interface
};
```