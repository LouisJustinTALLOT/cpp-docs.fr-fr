---
title: Avertissement du compilateur (niveau 1) C4812
ms.date: 11/04/2016
f1_keywords:
- C4812
helpviewer_keywords:
- C4812
ms.assetid: a7f5721f-2019-44de-ad62-ed30bac8b1f3
ms.openlocfilehash: 420c44359b9e92cf8e77070bd3a270f992722d48
ms.sourcegitcommit: 458dcc794e3841919c01a3a5ff6b9a3767f8861b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/13/2019
ms.locfileid: "74051282"
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