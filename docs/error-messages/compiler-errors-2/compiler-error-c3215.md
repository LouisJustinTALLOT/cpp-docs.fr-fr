---
description: 'En savoir plus sur : erreur du compilateur C3215'
title: Erreur du compilateur C3215
ms.date: 11/04/2016
f1_keywords:
- C3215
helpviewer_keywords:
- C3215
ms.assetid: d0d16007-8885-42e0-b086-2d3a61f348c5
ms.openlocfilehash: 1291f480e4f01502db4232585f7e7786fd637072
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97173738"
---
# <a name="compiler-error-c3215"></a>Erreur du compilateur C3215

'type1' : paramètre de type générique déjà limité à 'type2'

Une contrainte a été spécifiée plusieurs fois.

Pour plus d’informations sur les types génériques, consultez [Generics](../../extensions/generics-cpp-component-extensions.md).

L’exemple suivant génère l’erreur C3215 :

```cpp
// C3215.cpp
// compile with: /clr
interface struct A {};

generic <class T>
where T : A,A
ref class C {};   // C3215
```

Solution possible :

```cpp
// C3215b.cpp
// compile with: /clr /c
interface struct A {};

generic <class T>
where T : A
ref class C {};
```
