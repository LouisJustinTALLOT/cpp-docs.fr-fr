---
description: 'En savoir plus sur : erreur du compilateur C2754'
title: Erreur du compilateur C2754
ms.date: 11/04/2016
f1_keywords:
- C2754
helpviewer_keywords:
- C2754
ms.assetid: 1cab66c5-da9d-4b81-b7fb-9cdc48ff1ccc
ms.openlocfilehash: 68840f85d7a7f9be18246dfa4f3176a76f0fb9ac
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97336224"
---
# <a name="compiler-error-c2754"></a>Erreur du compilateur C2754

'spécialisation' : une spécialisation partielle ne peut pas avoir un paramètre de modèle sans type dépendant

Une tentative a été faite pour spécialiser partiellement une classe de modèle qui a un paramètre de modèle sans type dépendant. Cette opération n’est pas autorisée.

L’exemple suivant génère l’C2754 :

```cpp
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
