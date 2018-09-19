---
title: Erreur du compilateur C2665 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2665
dev_langs:
- C++
helpviewer_keywords:
- C2665
ms.assetid: a7f99b61-2eae-4f2b-ba75-ea68fd1e8312
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b442e1de0481ef3d00742ed201575526332decff
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46109143"
---
# <a name="compiler-error-c2665"></a>Erreur du compilateur C2665

'fonction' : aucune des surcharges nombre1 peut convertir le paramètre nombre2 à partir du type 'type'

Un paramètre de la fonction surchargée ne peut pas être converti au type requis.  Solutions possibles :

- Fournissez un opérateur de conversion.

- Utilisez la conversion explicite.

## <a name="example"></a>Exemple

L’exemple suivant génère C2665.

```
// C2665.cpp
void func(short, char*){}
void func(char*, char*){}

int main() {
   func(0, 1);   // C2665
   func((short)0, (char*)1);   // OK
}
```