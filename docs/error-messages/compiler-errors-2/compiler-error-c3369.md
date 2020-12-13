---
description: 'En savoir plus sur : erreur du compilateur C3369'
title: Erreur du compilateur C3369
ms.date: 11/04/2016
f1_keywords:
- C3369
helpviewer_keywords:
- C3369
ms.assetid: c6ceb9cb-3df9-4334-9a5c-d16db351d476
ms.openlocfilehash: 0391dbd7fe80daf93c8070253181c40fb805fa82
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97150798"
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
