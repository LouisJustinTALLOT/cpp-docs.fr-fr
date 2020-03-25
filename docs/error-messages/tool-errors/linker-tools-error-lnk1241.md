---
title: Erreur des outils Éditeur de liens LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 6e2b955787166c94be4ca35e1c58df5becd243f2
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183811"
---
# <a name="linker-tools-error-lnk1241"></a>Erreur des outils Éditeur de liens LNK1241

fichier de ressources’fichier de ressources’déjà spécifié

Cette erreur est générée si vous exécutez **cvtres** manuellement à partir de la ligne de commande et si vous transmettez ensuite le fichier. obj résultant à l’éditeur de liens en plus des autres fichiers. res.

Pour spécifier plusieurs fichiers. res, transmettez-les tous à l’éditeur de liens en tant que fichiers. res, et non à partir de fichiers. obj créés par **cvtres**.
