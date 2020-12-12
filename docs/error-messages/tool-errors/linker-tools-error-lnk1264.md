---
description: 'En savoir plus sur : erreur des outils Éditeur de liens LNK1264'
title: Erreur des outils Éditeur de liens LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: 122186482800597780405ae89e8e01c008794756
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97193784"
---
# <a name="linker-tools-error-lnk1264"></a>Erreur des outils Éditeur de liens LNK1264

/LTCG : PGINSTRUMENT spécifié mais aucune génération de code requise ; échec de l’instrumentation

**/LTCG : PGINSTRUMENT** a été spécifié, mais aucun fichier. obj compilé avec [/GL](../../build/reference/gl-whole-program-optimization.md)n’a été trouvé. L’instrumentation ne peut pas avoir lieu et le lien a échoué. Il doit y avoir au moins un fichier. obj sur la ligne de commande qui est compilé avec **/GL** afin que l’instrumentation puisse se produire.

L’optimisation guidée par profil (PGO) est uniquement disponible dans les compilateurs 64 bits.
