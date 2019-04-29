---
title: Erreur du compilateur C3869
ms.date: 11/04/2016
f1_keywords:
- C3869
helpviewer_keywords:
- C3869
ms.assetid: 85b2ad72-95c1-4ed6-9761-6ef66c3802b7
ms.openlocfilehash: 1a3d0d754557bbc811d1017ed1491181333e82dc
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62242966"
---
# <a name="compiler-error-c3869"></a>Erreur du compilateur C3869

contrainte gcnew ne contient n’a pas de liste de paramètres vide '()'

Le `gcnew` contrainte spéciale a été spécifiée sans la liste de paramètres vide. Consultez [contraintes sur les paramètres de Type générique (C++ / c++ / CLI)](../../extensions/constraints-on-generic-type-parameters-cpp-cli.md) pour plus d’informations.

## <a name="example"></a>Exemple

L’exemple suivant génère C3869.

```
// C3869.cpp
// compile with: /c /clr
using namespace System;
generic <typename T>
where T : gcnew   // C3869
// try the following line instead
// where T : gcnew()
ref class List {};
```