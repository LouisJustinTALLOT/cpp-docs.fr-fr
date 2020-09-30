---
title: Erreur du compilateur C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: 3b2e6f38e93514154b20e674139a2d771dcf586e
ms.sourcegitcommit: a1676bf6caae05ecd698f26ed80c08828722b237
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/29/2020
ms.locfileid: "91503242"
---
# <a name="compiler-error-c3369"></a>Erreur du compilateur C3369

'module name' : idl_module déjà défini

L’utilisation d’ [idl_module](../../windows/attributes/idl-module.md) où vous définissez la DLL ne peut se produire qu’une seule fois dans un programme.

L’exemple suivant génère l’erreur C3369 :

```cpp
// C3369.cpp
// compile with: /c
[idl_module(name="name1", dllname="x.dll")]; // C3369
[idl_module(name="name1", dllname="x.dll")];
```
