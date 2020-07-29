---
title: Erreur du compilateur C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 7e6e07fb90827fb28fcdde2f723a36c4529a1868
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87225486"
---
# <a name="compiler-error-c2410"></a>Erreur du compilateur C2410

'identificateur' : nom de membre ambigu dans’Context'

L’identificateur est membre de plusieurs structures ou unions dans ce contexte.

Utilisez un spécificateur de structure ou d’Union sur l’opérande à l’origine de l’erreur. Un spécificateur de structure ou d’Union est un identificateur de type **`struct`** ou **`union`** (un **`typedef`** nom ou une variable du même type que la structure ou l’Union référencée). Le spécificateur doit être l’opérande gauche du premier opérateur de sélection de membres (.) pour utiliser l’opérande.
