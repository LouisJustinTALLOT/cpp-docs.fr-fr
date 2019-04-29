---
title: Avertissement NMAKE U4011
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 3b73e92c929b3dd5924584ab732f731d565d0430
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62359772"
---
# <a name="nmake-warning-u4011"></a>Avertissement NMAKE U4011

'target' : les dépendants pas tous disponibles ; cible non générée

Un dépendant de la cible spécifiée n’existe pas ou a été obsolète, et une commande de mise à jour du dépendant a renvoyé un code de sortie différent de zéro. L’option /K a indiqué NMAKE pour continuer le traitement des parties non liées de la génération et d’émettre un code de sortie 1 quand la session NMAKE est terminée.

Cet avertissement est précédé par l’avertissement [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) pour chaque dépendant qui n’a pas pu être créé ou mis à jour.