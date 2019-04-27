---
title: Erreur du compilateur C3747
ms.date: 11/04/2016
f1_keywords:
- C3747
helpviewer_keywords:
- C3747
ms.assetid: a9a4be67-5d9c-4dcc-9ae9-baae46cbecde
ms.openlocfilehash: 860a990e35b0d51dfc1316a11a2d2512eb40c273
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62226794"
---
# <a name="compiler-error-c3747"></a>Erreur du compilateur C3747

paramètre de type par défaut manquant : paramètre param

Les paramètres génériques ou de modèle avec les valeurs par défaut ne peut pas être suivies dans la liste de paramètres paramètres qui n’ont pas de valeurs par défaut.

L’exemple suivant génère l’erreur C3747 :

```
// C3747.cpp
template <class T1 = int, class T2>   // C3747
struct MyStruct {};
```

Solution possible :

```
// C3747b.cpp
// compile with: /c
template <class T1, class T2 = int>
struct MyStruct {};
```