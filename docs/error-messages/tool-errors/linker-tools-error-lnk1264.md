---
title: LNK1264 d’erreur des outils Éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1264
dev_langs:
- C++
helpviewer_keywords:
- LNK1264
ms.assetid: 23b1aad7-d382-42c1-bae8-db68575c57a8
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 8232e83774dc53755b77ad9c8b3bbb2a0bcc6ae6
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46102740"
---
# <a name="linker-tools-error-lnk1264"></a>Erreur des outils Éditeur de liens LNK1264

/ LTCG : PGINSTRUMENT spécifié mais aucune génération de code requise ; instrumentation a échoué

**/ LTCG : PGINSTRUMENT** a été spécifié mais aucun fichier .obj ont été trouvé qui ont été compilées avec [/GL](../../build/reference/gl-whole-program-optimization.md). Instrumentation ne peut pas avoir lieu et le lien a échoué. Il doit y avoir au moins un fichier .obj sur la ligne de commande qui est compilé avec **/GL** afin que l’instrumentation.

Optimisation guidée par profil (PGO) est uniquement disponible dans les compilateurs 64 bits.