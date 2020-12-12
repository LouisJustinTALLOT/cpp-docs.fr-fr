---
description: 'En savoir plus sur : erreur du compilateur C2815'
title: Erreur du compilateur C2815
ms.date: 11/04/2016
f1_keywords:
- C2815
helpviewer_keywords:
- C2815
ms.assetid: d0256fd6-0721-4c99-b03c-52d96e77a613
ms.openlocfilehash: fd0ee162c10acd89e4746ea906d64ea8ef069271
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97194837"
---
# <a name="compiler-error-c2815"></a>Erreur du compilateur C2815

'operator delete' : le premier paramètre formel doit être’void * ', mais’param’a été utilisé

Toute fonction d' [opérateur delete](../../standard-library/new-operators.md#op_delete) définie par l’utilisateur doit accepter un premier paramètre formel de type `void *` .

L’exemple suivant génère l’C2815 :

```cpp
// C2815.cpp
// compile with: /c
class CMyClass {
public:
   void mf1(int *a);
   void operator delete(CMyClass *);   // C2815
   void operator delete(void *);
};
```
