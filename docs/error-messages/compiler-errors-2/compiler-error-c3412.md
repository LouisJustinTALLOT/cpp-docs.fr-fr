---
description: 'En savoir plus sur : erreur du compilateur C3412'
title: Erreur du compilateur C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: aa0dc6cfeac193afc99d003cd821663bcfc139c8
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97313188"
---
# <a name="compiler-error-c3412"></a>Erreur du compilateur C3412

'template' : impossible de spécialiser le modèle dans la portée actuelle

Un modèle ne peut pas être spécialisé au niveau de la portée de la classe, uniquement dans la portée globale ou de l’espace de noms.

## <a name="examples"></a>Exemples

L’exemple suivant génère l’C3412.

```cpp
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

L’exemple suivant illustre une résolution possible.

```cpp
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```
