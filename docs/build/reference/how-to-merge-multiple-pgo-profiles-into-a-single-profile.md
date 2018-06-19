---
title: 'Comment : fusionner plusieurs profils PGO en un seul profil | Documents Microsoft'
ms.custom: ''
ms.date: 03/14/2018
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 6ca8fd6ef94af290d568f3186747c659b918c0fd
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372280"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Comment : fusionner plusieurs profils PGO en un seul profil

L’optimisation guidée par profil (PGO) est un excellent outil pour la création des fichiers binaires optimisés basées sur un scénario de profilage. Mais que se passe-t-il si vous avez une application qui a plusieurs scénarios importants, mais distincts ? Comment créer un profil unique que PGO peut utiliser à partir de différents scénarios ? Dans Visual Studio, le Gestionnaire de PGO, [pgomgr.exe](pgomgr.md), cette tâche.

La syntaxe pour fusionner les profils est :

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

où `num` est une pondération facultative à utiliser pour les fichiers .pgc ajoutés par cette fusion. Poids sont couramment utilisées si certains scénarios sont plus importants que d’autres personnes ou s’il existe des scénarios qui doivent être exécutées plusieurs fois.

> [!NOTE]
> Le Gestionnaire de PGO ne fonctionne pas avec les données de profil périmées. Pour fusionner un fichier .pgc dans un fichier .pgd, le fichier .pgc doit être généré par un fichier exécutable qui a été créé par le même appel de lien qui a généré le fichier .pgd.

## <a name="examples"></a>Exemples

Dans cet exemple, le PGO Manager ajoute pgcFile.pgc à pgdFile.pgd six fois :

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

Dans cet exemple, le PGO Manager ajoute pgcFile1.pgc et pgcFile2.pgc à pgdFile.pgd, deux fois pour chaque fichier .pgc :

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Si le PGO Manager est exécuté sans arguments fichier .pgc, il recherche le répertoire local pour tous les fichiers .pgc ayant le même nom que le fichier .pgd suivi d’un point d’exclamation ( !) et des caractères arbitraires puis un ou plusieurs. Par exemple, si le répertoire local comporte des fichiers test.pgd, test ! 1.pgc, test2.pgc et test, et la commande suivante est exécutée à partir du répertoire local, puis **pgomgr** fusionne test ! 1.pgc et test test.pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](../../build/reference/profile-guided-optimizations.md)
