---
title: Erreur du compilateur C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 8b01a2f7b9c55fb57c880df5033538f4e45f76b4
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50643688"
---
# <a name="compiler-error-c2410"></a>Erreur du compilateur C2410

'identificateur' : nom de membre ambigu dans 'contexte'

L’identificateur est un membre de plus d’une structure ou union dans ce contexte.

Utiliser un spécificateur d’union ou de structure sur l’opérande qui a provoqué l’erreur. Un spécificateur d’union ou de structure est un identificateur de type `struct` ou `union` (un `typedef` nom ou une variable du même type que la structure ou union référencée). Le spécificateur doit être l’opérande gauche du premier opérateur de sélection de membres (.) à utiliser l’opérande.