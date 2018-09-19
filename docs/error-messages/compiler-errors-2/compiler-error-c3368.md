---
title: Erreur du compilateur C3368 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3368
dev_langs:
- C++
helpviewer_keywords:
- C3368
ms.assetid: 5bfd5be4-dfa9-4b33-9612-010561b40955
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 236bfdfc031544e05d4aa95d9c36720ddb0ebdf8
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46051293"
---
# <a name="compiler-error-c3368"></a>Erreur du compilateur C3368

'function declaration' : convention d’appel non valide pour IDL

Vous pouvez seulement utiliser les conventions d’appel [__stdcall](../../cpp/stdcall.md) ou [__cdecl](../../cpp/cdecl.md) dans un fichier .idl.

L’exemple suivant génère l’erreur C3368 :

```
// C3368.cpp
// processor: x86
[idl_module(name="Name", dllname="Some.dll")];

[idl_module(name="Name")]
int __fastcall f1();   // C3368
```