---
title: Erreur des outils Éditeur de liens LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: ca17b6946b9e988507af2786825223e042356d0e
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50505090"
---
# <a name="linker-tools-error-lnk1264"></a>Erreur des outils Éditeur de liens LNK1264

/ LTCG : PGINSTRUMENT spécifié mais aucune génération de code requise ; instrumentation a échoué

**/ LTCG : PGINSTRUMENT** a été spécifié mais aucun fichier .obj ont été trouvé qui ont été compilées avec [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentation ne peut pas avoir lieu et le lien a échoué. Il doit y avoir au moins un fichier .obj sur la ligne de commande qui est compilé avec **/GL** afin que l’instrumentation.

Optimisation guidée par profil (PGO) est uniquement disponible dans les compilateurs 64 bits.