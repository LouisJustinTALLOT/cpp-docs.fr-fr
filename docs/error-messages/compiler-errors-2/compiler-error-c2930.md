---
title: Erreur du compilateur C2930
ms.date: 11/04/2016
f1_keywords:
- C2930
helpviewer_keywords:
- C2930
ms.assetid: f07eecd1-e5d1-4518-bd89-b1fd2a003a17
ms.openlocfilehash: 20fa3e81e66bb30bd63e579a863b6071de4ef871
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50434825"
---
# <a name="compiler-error-c2930"></a>Erreur du compilateur C2930

'class' : type-class-id redéfini comme énumérateur de 'enum identifier'

Vous ne pouvez pas utiliser une classe générique ni de modèle en tant que membre d’une énumération.

Cette erreur peut être provoquée par une mise en correspondance incorrecte des accolades.

L’exemple suivant génère l’erreur C2930 :

```
// C2930.cpp
// compile with: /c
template<class T>
class x{};
enum SomeEnum { x };   // C2930

class y{};
enum SomeEnum { y };
```

L’erreur C2930 peut également se produire lors de l’utilisation de génériques :

```
// C2930c.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
enum SomeEnum { GC };   // C2930

ref struct GC2 {};
enum SomeEnum2 { GC2 };
```