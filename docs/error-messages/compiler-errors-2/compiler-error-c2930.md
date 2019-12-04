---
title: Erreur du compilateur C2930
ms.date: 11/04/2016
f1_keywords:
- C2930
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
ms.openlocfilehash: b30e614236298cf9a07cbc29e028039903f9748f
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74760978"
---
# <a name="compiler-error-c2930"></a>Erreur du compilateur C2930

'class' : type-class-id redéfini comme énumérateur de 'enum identifier'

Vous ne pouvez pas utiliser une classe générique ni de modèle en tant que membre d’une énumération.

Cette erreur peut se produire si des accolades sont appariées incorrectement.

L’exemple suivant génère l’erreur C2930 :

```cpp
// C2930.cpp
// compile with: /c
template<class T>
class x{};
enum SomeEnum { x };   // C2930

class y{};
enum SomeEnum { y };
```

L’erreur C2930 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2930c.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
enum SomeEnum { GC };   // C2930

ref struct GC2 {};
enum SomeEnum2 { GC2 };
```
