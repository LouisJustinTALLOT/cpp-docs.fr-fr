---
title: Erreur des outils Éditeur de liens LNK1264
ms.date: 11/04/2016
f1_keywords:
- LNK1264
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
ms.openlocfilehash: 00041e677ac7b69df9981551ee3b6cc18f9eb33d
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183759"
---
# <a name="linker-tools-error-lnk1264"></a>Erreur des outils Éditeur de liens LNK1264

/LTCG : PGINSTRUMENT spécifié mais aucune génération de code requise ; échec de l’instrumentation

**/LTCG : PGINSTRUMENT** a été spécifié, mais aucun fichier. obj compilé avec [/GL](../../build/reference/gl-whole-program-optimization.md)n’a été trouvé. L’instrumentation ne peut pas avoir lieu et le lien a échoué. Il doit y avoir au moins un fichier. obj sur la ligne de commande qui est compilé avec **/GL** afin que l’instrumentation puisse se produire.

L’optimisation guidée par profil (PGO) est uniquement disponible dans les compilateurs 64 bits.
