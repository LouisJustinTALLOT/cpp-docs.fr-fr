---
title: 'Comment : fusionner plusieurs profils PGO en un seul profil'
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 04730524fa756b0c6f1e505f3610609bdec6262a
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50476542"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Comment : fusionner plusieurs profils PGO en un seul profil

Optimisation guidée par profil (PGO) est un excellent outil pour la création des fichiers binaires optimisés basés sur un scénario qui est profilé. Mais que se passe-t-il si vous avez une application qui a plusieurs scénarios importants, mais distincts ? Comment créer un profil unique que PGO peut utiliser à partir de différents scénarios ? Dans Visual Studio, le Gestionnaire de PGO, [pgomgr.exe](pgomgr.md), effectue cette tâche pour vous.

La syntaxe pour la fusion des profils est :

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

où `num` est une pondération facultative à utiliser pour les fichiers .pgc ajoutées par cette fusion. Poids sont couramment utilisés s’il existe certains scénarios qui sont plus importantes que d’autres personnes ou s’il existe des scénarios qui doivent être exécutés plusieurs fois.

> [!NOTE]
> Le Gestionnaire de PGO ne fonctionne pas avec les données de profil périmées. Pour fusionner un fichier .pgc dans un fichier .pgd, le fichier .pgc doit être généré par un exécutable qui a été créé par le même appel de lien qui a généré le fichier .pgd.

## <a name="examples"></a>Exemples

Dans cet exemple, le Gestionnaire de PGO ajoute pgcFile.pgc à pgdFile.pgd six fois :

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

Dans cet exemple, le Gestionnaire de PGO ajoute pgcFile1.pgc et pgcFile2.pgc à pgdFile.pgd, deux fois pour chaque fichier .pgc :

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Si le PGO Manager est exécuté sans arguments fichier .pgc, il recherche dans le répertoire local pour tous les fichiers .pgc ayant le même nom que le fichier .pgd suivi d’un point d’exclamation ( !) et des caractères arbitraires puis un ou plusieurs. Par exemple, si le répertoire local comporte des fichiers test.pgd, test ! 1.pgc, test2.pgc et test et exécuter la commande suivante à partir du répertoire local, puis **pgomgr** fusionne test ! 1.pgc et test test.pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](../../build/reference/profile-guided-optimizations.md)
