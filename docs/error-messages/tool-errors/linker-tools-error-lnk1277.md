---
title: Erreur des outils Éditeur de liens LNK1277
ms.date: 11/04/2016
f1_keywords:
- LNK1277
helpviewer_keywords:
- LNK1277
ms.assetid: afca3de0-50cc-4140-af7a-13493a170835
ms.openlocfilehash: 7c00fb32e4b36eff119195efbb34d536d80df6a9
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80183655"
---
# <a name="linker-tools-error-lnk1277"></a>Erreur des outils Éditeur de liens LNK1277

enregistrement de l’objet introuvable dans PGD (nom de fichier)

Lors de l’utilisation de [/LTCG : PGOPTIMZE](../../build/reference/ltcg-link-time-code-generation.md), le chemin d’accès de l’un des fichiers d’entrée. lib, def ou. obj était différent du chemin d’accès sur lequel ils ont été trouvés lors de l’utilisation de/LTCG : PGINSTRUMENT. Cela peut être expliqué par une modification de la variable d’environnement LIB après/LTCG : PGINSTRUMENT. Le chemin d’accès complet aux fichiers d’entrée est stocké dans le fichier. pgd.

/LTCG : PGOPTIMIZE exige que les entrées soient identiques à la phase/LTCG : PGINSTRUMENT.

Pour résoudre cet avertissement, effectuez l’une des opérations suivantes :

- Exécutez/LTCG : PGINSTRUMENT, relancez toutes les séries de tests, puis exécutez/LTCG : PGOPTIMIZE.

- Remplacez la variable d’environnement LIB par celle que vous avez rencontrée lors de l’exécution de/LTCG : PGINSTRUMENT.

Il n’est pas recommandé de contourner LNK1277 à l’aide de/LTCG : PGUPDATE.
