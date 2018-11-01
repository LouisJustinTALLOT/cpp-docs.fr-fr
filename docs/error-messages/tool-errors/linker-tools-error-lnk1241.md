---
title: Erreur des outils Éditeur de liens LNK1241
ms.date: 11/04/2016
f1_keywords:
- LNK1241
helpviewer_keywords:
- LNK1241
ms.assetid: 7b8b52eb-0231-4521-b52a-2bce8d3e8956
ms.openlocfilehash: 87f73680d7ed40b9b2db9f40f9140976d552ab6b
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50584546"
---
# <a name="linker-tools-error-lnk1241"></a>Erreur des outils Éditeur de liens LNK1241

fichier de ressources 'fichier de ressources' déjà spécifié

Cette erreur est générée si vous exécutez **cvtres** manuellement à partir de la ligne de commande et si vous passez le fichier .obj résultant de fichiers à l’éditeur de liens en outre d’autres fichiers .res.

Pour spécifier plusieurs fichiers .res, passez-les tous à l’éditeur de liens en tant que fichiers .res, et non depuis des fichiers .obj créés par **cvtres**.