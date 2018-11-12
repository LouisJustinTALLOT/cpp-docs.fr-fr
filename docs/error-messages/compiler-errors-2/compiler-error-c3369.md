---
title: Erreur du compilateur C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: 0cd27da4b73732513afe0bd33a2d7312e6ddbe97
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50618957"
---
# <a name="compiler-error-c3369"></a>Erreur du compilateur C3369

'module name' : idl_module déjà défini

L’utilisation d’ [idl_module](../../windows/idl-module.md) où vous définissez la DLL ne peut se produire qu’une seule fois dans un programme.

L’exemple suivant génère l’erreur C3369 :

```
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```