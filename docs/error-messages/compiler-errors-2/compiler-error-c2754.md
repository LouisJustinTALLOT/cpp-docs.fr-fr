---
title: Erreur du compilateur C2754
ms.date: 11/04/2016
f1_keywords:
- C2754
helpviewer_keywords:
- C2754
ms.assetid: 1cab66c5-da9d-4b81-b7fb-9cdc48ff1ccc
ms.openlocfilehash: cfe6f8faa1b00faf32ae53e6c25c23532c9f3a3f
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62228523"
---
# <a name="compiler-error-c2754"></a>Erreur du compilateur C2754

'specialization' : une spécialisation partielle ne peut pas avoir un paramètre de modèle sans type dépendant

Une tentative a été effectuée pour spécialiser partiellement une classe de modèle qui a un paramètre de modèle sans type dépendant. Cette opération n’est pas autorisée.

L’exemple suivant génère l’erreur C2754 :

```
// C2754.cpp
// compile with: /c

template<class T, T t>
struct A {};

template<class T, int N>
struct B {};

template<class T> struct A<T,5> {};   // C2754
template<> struct A<int,5> {};   // OK
template<class T> struct B<T,5> {};   // OK
```