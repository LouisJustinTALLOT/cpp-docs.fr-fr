---
title: Erreur du compilateur C3744 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C3744
dev_langs:
- C++
helpviewer_keywords:
- C3744
ms.assetid: a447d050-80d1-406a-9a6e-f15c527d717c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: d644a621fc6d8e460e1b97e5baec360de8662365
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46063721"
---
# <a name="compiler-error-c3744"></a>Erreur du compilateur C3744

__unhook doit avoir au moins 3 arguments pour les événements managés

Le [__unhook](../../cpp/unhook.md) fonction doit prendre trois paramètres lorsqu’il est utilisé dans un programme qui est compilé pour les Extensions managées pour C++.

`__hook` et `__unhook` ne sont pas compatibles avec la programmation /clr. Utilisez les opérateurs += et -= à la place.

C3744 est uniquement accessible à l’aide de l’option de compilateur obsolète **/CLR : oldSyntax**.
