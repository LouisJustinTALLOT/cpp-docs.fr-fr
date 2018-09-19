---
title: Erreur du compilateur C2410 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- C2410
dev_langs:
- C++
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ba4c2b57bcae062ccf811e33cf1deaea45f83737
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46052450"
---
# <a name="compiler-error-c2410"></a>Erreur du compilateur C2410

'identificateur' : nom de membre ambigu dans 'contexte'

L’identificateur est un membre de plus d’une structure ou union dans ce contexte.

Utiliser un spécificateur d’union ou de structure sur l’opérande qui a provoqué l’erreur. Un spécificateur d’union ou de structure est un identificateur de type `struct` ou `union` (un `typedef` nom ou une variable du même type que la structure ou union référencée). Le spécificateur doit être l’opérande gauche du premier opérateur de sélection de membres (.) à utiliser l’opérande.