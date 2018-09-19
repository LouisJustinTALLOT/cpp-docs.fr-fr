---
title: Erreur du compilateur C2705 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2705
dev_langs:
- C++
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1c0eefd19645ee6ac06664249f7953d904cd5896
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46093699"
---
# <a name="compiler-error-c2705"></a>Erreur du compilateur C2705

'étiquette' : saut dans la portée 'bloc gestionnaire d’exception' non conforme

L’exécution passe à une étiquette dans un `try` / `catch`, `__try` / `__except`, `__try` / `__finally` bloc. Pour plus d’informations, consultez l’article [Gestion des exceptions](../../cpp/exception-handling-in-visual-cpp.md).

L’exemple suivant génère l’erreur C2705 :

```
// C2705.cpp
int main() {
goto trouble;
   __try {
      trouble: ;   // C2705
   }
   __finally {}

   // try the following line instead
   // trouble: ;
}
```