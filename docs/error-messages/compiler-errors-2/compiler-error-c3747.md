---
title: Erreur du compilateur C3747
ms.date: 11/04/2016
f1_keywords:
- C3747
helpviewer_keywords:
- C3747
ms.assetid: a9a4be67-5d9c-4dcc-9ae9-baae46cbecde
ms.openlocfilehash: 761bb44f5097d998fd885fdb1c5caacf90db3642
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74761866"
---
# <a name="compiler-error-c3747"></a>Erreur du compilateur C3747

paramètre de type par défaut manquant : paramètre param

Les paramètres génériques ou de modèle avec des valeurs par défaut ne peuvent pas être suivis dans la liste de paramètres par des paramètres qui n’ont pas de valeurs par défaut.

L’exemple suivant génère l’C3747 :

```cpp
// C3747.cpp
template <class T1 = int, class T2>   // C3747
struct MyStruct {};
```

Solution possible :

```cpp
// C3747b.cpp
// compile with: /c
template <class T1, class T2 = int>
struct MyStruct {};
```
