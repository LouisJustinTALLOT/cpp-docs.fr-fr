---
title: Erreur du compilateur C2601 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2601
dev_langs:
- C++
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 522abe9c3cb4b9922a6b307055a3d85f40253793
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46062954"
---
# <a name="compiler-error-c2601"></a>Erreur du compilateur C2601

'fonction' : les définitions de fonction locale ne sont pas conformes

Code tente de définir une fonction dans une fonction.

Ou bien, il peut y avoir une accolade supplémentaire dans votre code source avant de l’emplacement de l’erreur C2601.

L’exemple suivant génère l’erreur C2601 :

```
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```