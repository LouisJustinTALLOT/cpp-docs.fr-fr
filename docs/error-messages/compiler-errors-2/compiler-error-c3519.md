---
title: Erreur du compilateur C3519
ms.date: 11/04/2016
f1_keywords:
- C3519
helpviewer_keywords:
- C3519
ms.assetid: ca24b2bc-7e90-4448-ae84-3fedddf9bca7
ms.openlocfilehash: e9a998e1c3a6c2fb770fb9d26d97b8a24e5554d3
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50432771"
---
# <a name="compiler-error-c3519"></a>Erreur du compilateur C3519

'param_non_valide' : paramètre non valide pour l’attribut embedded_idl

Un paramètre a été passé à la `embedded_idl` attribut de [#import](../../preprocessor/hash-import-directive-cpp.md), mais le compilateur n’a pas reconnu le paramètre.

Les seuls paramètres autorisés pour `embedded_idl` sont `emitidl` et `no_emitidl`.

L’exemple suivant génère l’erreur C3519 :

```
// C3519.cpp
// compile with: /LD
[module(name="MyLib2")];
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidcl")
// C3519
#import "C:\testdir\bin\importlib.tlb" embedded_idl("no_emitidl")
// OK
```