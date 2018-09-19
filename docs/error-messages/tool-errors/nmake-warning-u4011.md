---
title: Avertissement NMAKE U4011 | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- U4011
dev_langs:
- C++
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: a1038ee86f76789451565ab6799795c851c95a95
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46118334"
---
# <a name="nmake-warning-u4011"></a>Avertissement NMAKE U4011

'target' : les dépendants pas tous disponibles ; cible non générée

Un dépendant de la cible spécifiée n’existe pas ou a été obsolète, et une commande de mise à jour du dépendant a renvoyé un code de sortie différent de zéro. L’option /K a indiqué NMAKE pour continuer le traitement des parties non liées de la génération et d’émettre un code de sortie 1 quand la session NMAKE est terminée.

Cet avertissement est précédé par l’avertissement [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) pour chaque dépendant qui n’a pas pu être créé ou mis à jour.