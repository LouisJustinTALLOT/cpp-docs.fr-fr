---
title: Erreur du compilateur C3347
ms.date: 11/04/2016
f1_keywords:
- C3347
helpviewer_keywords:
- C3347
ms.assetid: e939ad29-0b78-4681-9618-9bdae5675cee
ms.openlocfilehash: 9f62d66148aa75040f7bab5ea69931d2ef9c474a
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74755614"
---
# <a name="compiler-error-c3347"></a>Erreur du compilateur C3347

'arg' : l’argument requis n’est pas spécifié dans l’attribut idl_module

Un argument obligatoire n’a pas été passé à l’attribut [idl_module](../../windows/idl-module.md) .

L’exemple suivant génère l’erreur C3347 :

```cpp
// C3347.cpp
// compile with: /c
[module(name="xx")];

[idl_module(dllname="x")];    // C3347
// try the following line instead
// [idl_module(name="test", dllname="x")];
```
