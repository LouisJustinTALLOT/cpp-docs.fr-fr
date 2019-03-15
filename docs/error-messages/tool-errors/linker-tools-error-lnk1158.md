---
title: Erreur des outils Éditeur de liens LNK1158
ms.date: 11/04/2016
f1_keywords:
- LNK1158
helpviewer_keywords:
- LNK1158
ms.assetid: 45febf16-d9e1-42db-af91-532e2717fd6a
ms.openlocfilehash: 0dbb40fb1fe0405f3685a5e7246ecba2b53ec526
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57812016"
---
# <a name="linker-tools-error-lnk1158"></a>Erreur des outils Éditeur de liens LNK1158

Impossible d’exécuter 'nom_fichier'

Le fichier exécutable donné appelé par [lien](../../build/reference/linking.md) n’est pas dans le répertoire qui contient le lien ni dans un répertoire spécifié dans la variable d’environnement PATH.

Par exemple, vous obtiendrez cette erreur si vous essayez d’utiliser le paramètre PGOPTIMIZE le [/LTCG](../../build/reference/ltcg-link-time-code-generation.md) option de l’éditeur de liens sur un ordinateur avec un système d’exploitation 32 bits.