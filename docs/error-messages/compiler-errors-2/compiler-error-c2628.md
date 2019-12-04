---
title: Erreur du compilateur C2628
ms.date: 11/04/2016
f1_keywords:
- C2628
helpviewer_keywords:
- C2628
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
ms.openlocfilehash: 4198d6ff0552f5280904ed1fea5e185df1a9c804
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74754717"
---
# <a name="compiler-error-c2628"></a>Erreur du compilateur C2628

'type1 'suivi de’type2 'n’est pas conforme (n’auriez-vous pas oublié un'; ' ?)

Il manque peut-être un point-virgule.

L’exemple suivant génère l’C2628 :

```cpp
// C2628.cpp
class CMyClass {}
int main(){}   // C2628 error
```

Solution possible :

```cpp
// C2628b.cpp
class CMyClass {};
int main(){}
```
