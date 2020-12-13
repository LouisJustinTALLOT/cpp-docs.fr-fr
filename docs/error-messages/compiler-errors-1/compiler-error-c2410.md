---
description: 'En savoir plus sur : erreur du compilateur C2410'
title: Erreur du compilateur C2410
ms.date: 11/04/2016
f1_keywords:
- C2410
helpviewer_keywords:
- C2410
ms.assetid: b69b2de1-56f3-4ebc-8913-04ac57ffe8a1
ms.openlocfilehash: 921ccdcff64bca28c3a771dd0931b8b7abf83e52
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97341891"
---
# <a name="compiler-error-c2410"></a>Erreur du compilateur C2410

'identificateur' : nom de membre ambigu dans’Context'

L’identificateur est membre de plusieurs structures ou unions dans ce contexte.

Utilisez un spécificateur de structure ou d’Union sur l’opérande à l’origine de l’erreur. Un spécificateur de structure ou d’Union est un identificateur de type **`struct`** ou **`union`** (un **`typedef`** nom ou une variable du même type que la structure ou l’Union référencée). Le spécificateur doit être l’opérande gauche du premier opérateur de sélection de membres (.) pour utiliser l’opérande.
