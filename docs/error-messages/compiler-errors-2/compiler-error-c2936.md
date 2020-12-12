---
description: 'En savoir plus sur : erreur du compilateur C2936'
title: Erreur du compilateur C2936
ms.date: 11/04/2016
f1_keywords:
- C2936
helpviewer_keywords:
- C2936
ms.assetid: 5d1ba0fc-0c78-4a37-a83b-1ef8527763be
ms.openlocfilehash: 2c01886ac02cdd772e7c92faa15dbd015aa6e6e9
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97323036"
---
# <a name="compiler-error-c2936"></a>Erreur du compilateur C2936

'class' : type-class-id redéfini comme variable globale de données

Vous ne pouvez pas utiliser une classe générique ni de modèle comme variable globale de données.

Cette erreur peut être provoquée par une mise en correspondance incorrecte des accolades.

L’exemple suivant génère l’erreur C2936 :

```cpp
// C2936.cpp
// compile with: /c
template<class T> struct TC { };
int TC<int>;   // C2936

// OK
struct TC2 { };
int TC2;
```

L’erreur C2936 peut également se produire lors de l’utilisation de génériques :

```cpp
// C2936b.cpp
// compile with: /clr /c
generic<class T>
ref struct GC {};
int GC<int>;   // C2936

// OK
ref struct GC2 {};
int GC2;
```
