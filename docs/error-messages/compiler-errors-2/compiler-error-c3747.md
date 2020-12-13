---
description: 'En savoir plus sur : erreur du compilateur C3747'
title: Erreur du compilateur C3747
ms.date: 11/04/2016
f1_keywords:
- C3747
helpviewer_keywords:
- C3747
ms.assetid: a9a4be67-5d9c-4dcc-9ae9-baae46cbecde
ms.openlocfilehash: 9e40b887d5a107eed5e93a7f3827ba4e8c1590e4
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97340201"
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
