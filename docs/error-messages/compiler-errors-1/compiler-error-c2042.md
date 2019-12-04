---
title: Erreur du compilateur C2042
ms.date: 11/04/2016
f1_keywords:
- C2042
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
ms.openlocfilehash: 6bc66f5b3a7bd669ef06cac3b53631ff7948e8ad
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74740388"
---
# <a name="compiler-error-c2042"></a>Erreur du compilateur C2042

les mots clés signed/unsigned s'excluent mutuellement

Les mots clés `signed` et `unsigned` sont utilisés dans une même déclaration.

L’exemple suivant génère l’erreur C2042 :

```cpp
// C2042.cpp
unsigned signed int i;   // C2042
```

Solution possible :

```cpp
// C2042b.cpp
// compile with: /c
unsigned int i;
signed int ii;
```
