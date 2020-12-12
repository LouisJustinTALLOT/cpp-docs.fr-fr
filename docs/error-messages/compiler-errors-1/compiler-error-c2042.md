---
description: 'En savoir plus sur : erreur du compilateur C2042'
title: Erreur du compilateur C2042
ms.date: 11/04/2016
f1_keywords:
- C2042
helpviewer_keywords:
- C2042
ms.assetid: e111788f-41ce-405a-9824-a4c1c26059e6
ms.openlocfilehash: 3dd4ae7471997e518c854d570b4a2e3aa4ec3856
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175207"
---
# <a name="compiler-error-c2042"></a>Erreur du compilateur C2042

les mots clés signed/unsigned s'excluent mutuellement

Les mots clés **`signed`** et **`unsigned`** sont utilisés dans une déclaration unique.

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
