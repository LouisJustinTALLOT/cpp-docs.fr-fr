---
description: 'En savoir plus sur : erreur du compilateur C2033'
title: Erreur du compilateur C2033
ms.date: 11/04/2016
f1_keywords:
- C2033
helpviewer_keywords:
- C2033
ms.assetid: fd5a1637-9db2-4c98-a7cc-b63b39737cd9
ms.openlocfilehash: c7beabafb544f1ad76f6a8eabe24bd20a7e63f62
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97175428"
---
# <a name="compiler-error-c2033"></a>Erreur du compilateur C2033

'identifier' : un champ de bits ne peut pas avoir d’indirection

Le champ de bits a été déclaré en tant que pointeur, ce qui n’est pas autorisé.

L’exemple suivant génère l’erreur C2033 :

```cpp
// C2033.cpp
struct S {
   int *b : 1;  // C2033
};
```

Solution possible :

```cpp
// C2033b.cpp
// compile with: /c
struct S {
   int b : 1;
};
```
