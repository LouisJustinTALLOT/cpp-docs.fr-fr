---
title: Erreur du compilateur C2705
ms.date: 11/04/2016
f1_keywords:
- C2705
helpviewer_keywords:
- C2705
ms.assetid: 29249ea3-4ea7-4105-944b-bdb83e8d6852
ms.openlocfilehash: 1cd46db8e4cb237bebd9568409ecadf0ff84cdf8
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74758305"
---
# <a name="compiler-error-c2705"></a>Erreur du compilateur C2705

'étiquette' : saut non conforme dans la portée’bloc de gestionnaire d’exceptions'

L’exécution passe à une étiquette au sein d’un `try`/`catch`, `__try`/`__except`, `__try`/bloc `__finally`. Pour plus d’informations, consultez l’article [Gestion des exceptions](../../cpp/exception-handling-in-visual-cpp.md).

L’exemple suivant génère l’C2705 :

```cpp
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
