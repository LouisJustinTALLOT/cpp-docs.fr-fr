---
description: 'En savoir plus sur : erreur du compilateur C2130'
title: Erreur du compilateur C2130
ms.date: 11/04/2016
f1_keywords:
- C2130
helpviewer_keywords:
- C2130
ms.assetid: c6fd5a7e-8f28-4f67-99d1-95a13b0dff90
ms.openlocfilehash: 78e7b756d5902562c6093e3f26f9934e87e732ff
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323179"
---
# <a name="compiler-error-c2130"></a>Erreur du compilateur C2130

\#la ligne attendait une chaîne contenant le nom de fichier, 'Token’trouvé

Le jeton de nom de fichier facultatif [#line](../../preprocessor/hash-line-directive-c-cpp.md) `linenumber` doit être une chaîne.

L’exemple suivant génère l’erreur C2130 :

```cpp
// C2130.cpp
int main() {
   #line 1000 test   // C2130
   #line 1000 "test"   // OK
}
```
