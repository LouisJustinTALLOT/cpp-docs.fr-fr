---
description: 'En savoir plus sur : erreur du compilateur C2628'
title: Erreur du compilateur C2628
ms.date: 11/04/2016
f1_keywords:
- C2628
helpviewer_keywords:
- C2628
ms.assetid: 19a25e77-d5be-4107-88d5-0745b6281f98
ms.openlocfilehash: 876e96bfb406262c150807e4e95f14dd5b7177d5
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97123563"
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
