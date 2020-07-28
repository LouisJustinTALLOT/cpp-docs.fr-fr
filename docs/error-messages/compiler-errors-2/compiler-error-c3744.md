---
title: Erreur du compilateur C3744
ms.date: 11/04/2016
f1_keywords:
- C3744
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
ms.openlocfilehash: 8db81afc348434e9ea2f57c991962fb15dc6bf98
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87220156"
---
# <a name="compiler-error-c3744"></a>Erreur du compilateur C3744

__unhook doit avoir au moins 3 arguments pour les événements managés

La [`__unhook`](../../cpp/unhook.md) fonction doit prendre trois paramètres lorsqu’elle est utilisée dans un programme qui est compilé pour extensions managées pour C++.

**`__hook`** et ne **`__unhook`** sont pas compatibles avec la **`/clr`** programmation. Utilisez les opérateurs + = et-= à la place.

C3744 est accessible uniquement à l’aide de l’option de compilateur obsolète **`/clr:oldSyntax`** .
