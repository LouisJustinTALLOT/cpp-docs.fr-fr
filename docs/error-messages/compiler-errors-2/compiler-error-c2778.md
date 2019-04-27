---
title: Erreur du compilateur C2778
ms.date: 11/04/2016
f1_keywords:
- C2778
helpviewer_keywords:
- C2778
ms.assetid: b24cb732-2914-42cc-8928-e2d87b393428
ms.openlocfilehash: 56c316ac971d0bdd1a0ca27ef8d4282acbe24779
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62227674"
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