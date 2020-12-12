---
description: 'En savoir plus sur : avertissement du compilateur (niveau 1) C4812'
title: Avertissement du compilateur (niveau 1) C4812
ms.date: 11/04/2016
f1_keywords:
- C4812
helpviewer_keywords:
- C4812
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
ms.openlocfilehash: 3476086d067b98a62ec9d96647a77c109c9a263b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97332190"
---
# <a name="compiler-warning-level-1-c4812"></a>Avertissement du compilateur (niveau 1) C4812

style de déclaration obsolète : utilisez 'nouvelle_syntaxe' à la place

Dans la version actuelle de Visual C++, la spécialisation du constructeur explicite est toujours prise en charge, mais elle ne le sera peut être plus dans les versions ultérieures.

L’exemple suivant génère l’erreur C4812 :

```cpp
// C4812.cpp
// compile with: /W1 /c
template <class T>
class MyClass;

template<class T>
class MyClass<T*> {
   MyClass();
};

template<class T>
MyClass<T*>::MyClass<T*>() {}   // C4812
// try the following line instead
// MyClass<T*>::MyClass() {}
```
