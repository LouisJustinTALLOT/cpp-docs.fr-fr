---
title: Erreur du compilateur C2891
ms.date: 11/04/2016
f1_keywords:
- C2891
helpviewer_keywords:
- C2891
ms.assetid: e12cfb2d-df45-4b0d-b155-c51d17e812fa
ms.openlocfilehash: 2544cfc9e8cff283a7c3e0ace499408bb84cd046
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80201633"
---
# <a name="compiler-error-c2891"></a>Erreur du compilateur C2891

'paramètre' : impossible de prendre l’adresse d’un paramètre de modèle

Vous ne pouvez pas prendre l’adresse d’un paramètre de modèle, sauf s’il s’agit d’une lvalue. Les paramètres de type ne sont pas lvalues, car ils n’ont pas d’adresse. Les valeurs non-type dans les listes de paramètres de modèle qui ne sont pas lvalues n’ont pas non plus d’adresse. Il s’agit d’un exemple de code qui provoque l’erreur du compilateur C2891, car la valeur passée comme paramètre de modèle est une copie générée par le compilateur de l’argument template.

```
template <int i> int* f() { return &i; }
```

Les paramètres de modèle qui sont lvalues, tels que les types de référence, peuvent avoir leur adresse.

```
template <int& r> int* f() { return &r; }
```

Pour corriger cette erreur, ne prenez pas l’adresse d’un paramètre de modèle, sauf s’il s’agit d’une lvalue.
