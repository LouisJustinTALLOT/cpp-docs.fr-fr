---
title: Erreur du compilateur C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: ad241b656464746333760cfcbc134c91e49bf44e
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761414"
---
# <a name="compiler-error-c3412"></a>Erreur du compilateur C3412

'template' : impossible de spécialiser le modèle dans la portée actuelle

Un modèle ne peut pas être spécialisé au niveau de la portée de la classe, uniquement dans la portée globale ou de l’espace de noms.

## <a name="example"></a>Exemple

L’exemple suivant génère l’C3412.

```cpp
// C3412.cpp
template <class T>
struct S {
   template <>
   struct S<int> {};   // C3412 in a class
};
```

## <a name="example"></a>Exemple

L’exemple suivant illustre une résolution possible.

```cpp
// C3412b.cpp
// compile with: /c
template <class T>
struct S {};

template <>
struct S<int> {};
```
