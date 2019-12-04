---
title: Erreur du compilateur C3519
ms.date: 11/04/2016
f1_keywords:
- C3519
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
ms.openlocfilehash: 7e56ff814b1a2dd6ec3cb41db2cbcc21d7dcf2d9
ms.sourcegitcommit: 16fa847794b60bf40c67d20f74751a67fccb602e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/03/2019
ms.locfileid: "74750167"
---
# <a name="compiler-error-c3519"></a>Erreur du compilateur C3519

'invalid_param' : paramètre non valide pour l’attribut embedded_idl

Un paramètre a été passé à l’attribut `embedded_idl` de [#import](../../preprocessor/hash-import-directive-cpp.md), mais le compilateur n’a pas reconnu le paramètre.

Les seuls paramètres autorisés pour `embedded_idl` sont `emitidl` et `no_emitidl`.

L’exemple suivant génère l’C3519 :

```cpp
// C3519.cpp
// compile with: /LD
[module(name="MyLib2")];
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")
// C3519
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")
// OK
```
