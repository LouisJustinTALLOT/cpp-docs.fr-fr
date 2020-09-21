---
title: Erreur du compilateur C3412
ms.date: 11/04/2016
f1_keywords:
- C3412
helpviewer_keywords:
- C3412
ms.assetid: aa4dd43b-54ce-4cda-85c1-1a77dd6e34fa
ms.openlocfilehash: 6918e3be0a0288bab50d63a188bc33df87fe7754
ms.sourcegitcommit: 72161bcd21d1ad9cc3f12261aa84a5b026884afa
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2020
ms.locfileid: "90742890"
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
