---
title: Erreur du compilateur C2766
ms.date: 11/04/2016
f1_keywords:
- C2766
helpviewer_keywords:
- C2766
ms.assetid: 8032f4ca-6827-4f04-9c61-c44643c85cc4
ms.openlocfilehash: 87ea9f693265080d744746c6a8014b2b8b6db13a
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62257554"
---
# <a name="compiler-error-c2766"></a>Erreur du compilateur C2766

spécialisation explicite ; 'specialization' a déjà été définie

Les spécialisations explicites en double ne sont pas autorisées. Pour plus d’informations, consultez [spécialisation explicite des modèles de fonction](../../cpp/explicit-specialization-of-function-templates.md).

L’exemple suivant génère l’erreur C2766 :

```
// C2766.cpp
// compile with: /c
template<class T>
struct A {};

template<>
struct A<int> {};

template<>
struct A<int> {};   // C2766
// try the following line instead
// struct A<char> {};
```