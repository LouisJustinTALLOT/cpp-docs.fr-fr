---
title: Erreur du compilateur C2778 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2778
dev_langs:
- C++
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6106832ea82531a6f6915417ac56d53504db882e
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46022160"
---
# <a name="compiler-error-c2778"></a>Erreur du compilateur C2778

GUID incorrectement formé dans __declspec(uuid())

Un GUID incorrect est fourni à la [uuid](../../cpp/uuid-cpp.md) attributs étendus.

Le GUID doit être une chaîne de nombres hexadécimaux au format suivant :

```
// C2778a.cpp
// compile with: /c
struct __declspec(uuid("00000000-0000-0000-0000-000000000000")) A {};
struct __declspec(uuid("{00000000-0000-0000-0000-000000000000}")) B{};
```

Le `uuid` attributs étendus accepte les chaînes reconnues par [CLSIDFromString](/windows/desktop/api/combaseapi/nf-combaseapi-clsidfromstring), avec ou sans délimiteurs d’accolades.

L’exemple suivant génère l’erreur C2778 :

```
// C2778b.cpp
struct __declspec(uuid(" 00000000-0000-0000-0000-000000000000 ")) C { };   // C2778
struct __declspec(uuid("00000000000000000000000000000000")) D { };   // C2778
```