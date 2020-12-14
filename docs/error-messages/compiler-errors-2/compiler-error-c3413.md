---
description: 'En savoir plus sur : erreur du compilateur C3413'
title: Erreur du compilateur C3413
ms.date: 11/04/2016
f1_keywords:
- C3413
helpviewer_keywords:
- C3413
ms.assetid: de6c9b05-c373-4bd8-8cb0-12c2cd2e5674
ms.openlocfilehash: 1b6f5ba895ce1db433fb8c8366e62ab3c0790f84
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97316243"
---
# <a name="compiler-error-c3413"></a>Erreur du compilateur C3413

'nom' : instanciation explicite non valide

Le compilateur a détecté une instanciation explicite incorrecte.

L’exemple suivant génère l’erreur C3413 :

```cpp
// C3413.cpp
template
class MyClass {};   // C3413
```

Solution possible :

```cpp
// C3413b.cpp
// compile with: /c
template <class T>
class MyClass {};

template <>
class MyClass<int> {};
```
