---
description: 'En savoir plus sur : erreur du compilateur C2601'
title: Erreur du compilateur C2601
ms.date: 11/04/2016
f1_keywords:
- C2601
helpviewer_keywords:
- C2601
ms.assetid: 88275582-5f37-45d7-807d-05f06ba00965
ms.openlocfilehash: 373ba519633034ddf63889eb82cd71dccfa4a743
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97119994"
---
# <a name="compiler-error-c2601"></a>Erreur du compilateur C2601

'fonction' : les définitions de fonctions locales ne sont pas conformes

Le code tente de définir une fonction dans une fonction.

Ou bien, il peut y avoir une accolade supplémentaire dans votre code source avant l’emplacement de l’erreur C2601.

L’exemple suivant génère l’C2601 :

```cpp
// C2601.cpp
int main() {
   int i = 0;

   void funcname(int j) {   // C2601
      j++;
   }
}
```
