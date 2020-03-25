---
title: Erreur des outils Éditeur de liens LNK1158
ms.date: 11/04/2016
f1_keywords:
- LNK1158
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
ms.openlocfilehash: 2602c488db660ce067c672df4a746c388d987120
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80184058"
---
# <a name="linker-tools-error-lnk1158"></a>Erreur des outils Éditeur de liens LNK1158

Impossible d’exécuter’nom_fichier'

Le fichier exécutable donné appelé par [Link](../../build/reference/linking.md) n’est pas dans le répertoire qui contient le lien ni dans un répertoire spécifié dans la variable d’environnement PATH.

Par exemple, vous obtiendrez cette erreur si vous essayez d’utiliser le paramètre PGOPTIMIZE à l’option de l’éditeur de liens [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) sur un ordinateur doté d’un système d’exploitation 32 bits.
