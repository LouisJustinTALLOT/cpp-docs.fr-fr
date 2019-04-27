---
title: Erreur du compilateur C2628
ms.date: 11/04/2016
f1_keywords:
- C2628
helpviewer_keywords:
- C2628
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
ms.openlocfilehash: 90df41ba8ae85e57e40848f8b50f4c1df7c7b541
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62222921"
---
# <a name="compiler-error-c2628"></a>Erreur du compilateur C2628

'type1' suivi de 'type2' n’est pas conforme (n’auriez-vous pas oublié un ';' ?)

Un point-virgule est peut-être manquant.

L’exemple suivant génère l’erreur C2628 :

```
// C2628.cpp
class CMyClass {}
int main(){}   // C2628 error
```

Solution possible :

```
// C2628b.cpp
class CMyClass {};
int main(){}
```