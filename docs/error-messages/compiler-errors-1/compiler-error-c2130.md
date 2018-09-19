---
title: Erreur du compilateur C2130 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2130
dev_langs:
- C++
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 954930522651fcee6c29bf019f366e056fe681ef
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46071523"
---
# <a name="compiler-error-c2130"></a>Erreur du compilateur C2130

\#ligne attendait une chaîne contenant le nom de fichier, trouvé : 'token'

Le jeton de nom de fichier facultatif [#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` doit être une chaîne.

L’exemple suivant génère l’erreur C2130 :

```
// C2130.cpp
int main() {
   #line 1000 test   // C2130
   #line 1000 "test"   // OK
}
```