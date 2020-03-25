---
title: Avertissement NMAKE U4011
ms.date: 11/04/2016
f1_keywords:
- U4011
helpviewer_keywords:
- U4011
ms.assetid: e8244514-eba6-4285-8853-7baeefdcd8a4
ms.openlocfilehash: 6b1701ffc83f849d2482bd14b25d65c04c496899
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80193145"
---
# <a name="nmake-warning-u4011"></a>Avertissement NMAKE U4011

'target' : tous les dépendants ne sont pas disponibles ; cible non générée

Un dépendant de la cible donnée n’existe pas ou est obsolète, et une commande de mise à jour du dépendant a retourné un code de sortie différent de zéro. L’option/K a indiqué à NMAKE de poursuivre le traitement des parties non liées de la build et d’émettre un code de sortie 1 lorsque la session NMAKE est terminée.

Cet avertissement est précédé d’un avertissement [U4010](../../error-messages/tool-errors/nmake-warning-u4010.md) pour chaque dépendant qui n’a pas pu être créé ou mis à jour.
