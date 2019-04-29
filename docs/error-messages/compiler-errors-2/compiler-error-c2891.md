---
title: Erreur du compilateur C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: d9a1cdafdf7d3a2843aee4a20f71c7e6a4693150
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62366366"
---
# <a name="compiler-error-c2891"></a>Erreur du compilateur C2891

'paramètre' : ne peut pas prendre l’adresse d’un paramètre de modèle

Vous ne pouvez pas prendre l’adresse d’un paramètre de modèle, sauf si elle est une lvalue. Paramètres de type ne sont pas des lvalues, car ils n’ont aucun adresse. Également, les valeurs non-type dans les listes de paramètres de modèle qui ne sont pas des lvalues n’ont pas d’une adresse. Il s’agit d’un exemple de code qui provoque l’erreur du compilateur C2891, étant donné que la valeur passée comme paramètre de modèle est une copie générée par le compilateur de l’argument de modèle.

```
template <int i> int* f() { return &i; }
```

Paramètres de modèle qui sont des lvalues, tels que les types référence, peut avoir leur adresse prises.

```
template <int& r> int* f() { return &r; }
```

Pour corriger cette erreur, ne prennent pas l’adresse d’un paramètre de modèle, sauf si elle est une lvalue.