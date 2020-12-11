---
description: 'En savoir plus sur : Comment : fusionner plusieurs profils PGO en un seul profil'
title: 'Comment : fusionner plusieurs profils PGO en un seul profil'
ms.date: 03/14/2018
helpviewer_keywords:
- merging profiles
- profile-guided optimizations, merging profiles
ms.assetid: aab686b5-59dd-40d1-a04b-5064690f65a6
ms.openlocfilehash: 9549b9a26b0c16300c3750159f2c18c74dd293b0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97162688"
---
# <a name="how-to-merge-multiple-pgo-profiles-into-a-single-profile"></a>Comment : fusionner plusieurs profils PGO en un seul profil

L’optimisation guidée par profil (PGO) est un outil formidable pour créer des binaires optimisés basés sur un scénario profilé. Mais que se passe-t-il si vous avez une application qui comporte plusieurs scénarios importants et néanmoins distincts ? Comment créer un profil unique que PGO peut utiliser à partir de différents scénarios ? Dans Visual Studio, PGO Manager, [pgomgr.exe](pgomgr.md), fait ce travail pour vous.

La syntaxe de la fusion des profils est la suivante :

`pgomgr /merge[:num] [.pgc_files] .pgd_files`

où `num` est un poids facultatif à utiliser pour les fichiers. PGC ajoutés par cette fusion. Les pondérations sont généralement utilisées si certains scénarios sont plus importants que d’autres ou s’il existe des scénarios qui doivent être exécutés plusieurs fois.

> [!NOTE]
> PGO Manager ne fonctionne pas avec les données de profil périmées. Pour fusionner un fichier. PGC dans un fichier. pgd, le fichier. PGC doit être généré par un fichier exécutable qui a été créé par le même appel de lien qui a généré le fichier. pgd.

## <a name="examples"></a>Exemples

Dans cet exemple, PGO Manager ajoute pgcFile. PGC à pgdFile. pgd six fois :

`pgomgr /merge:6 pgcFile.pgc pgdFile.pgd`

Dans cet exemple, PGO Manager ajoute pgcFile1. pgc et pgcFile2. PGC à pgdFile. pgd, deux fois pour chaque fichier. PGC :

`pgomgr /merge:2 pgcFile1.pgc pgcFile2.pgc pgdFile.pgd`

Si le gestionnaire PGO est exécuté sans arguments de fichier. PGC, il recherche dans le répertoire local tous les fichiers. PGC qui ont le même nom de base que le fichier. pgd suivi d’un point d’exclamation ( !), puis d’un ou plusieurs caractères arbitraires. Par exemple, si le répertoire local contient des fichiers test. pgd, test ! 1. PGC, test2. pgc et test ! hello. PGC, et que la commande suivante est exécutée à partir du répertoire local, **pgomgr** fusionne test ! 1. pgc et test ! hello. PGC dans test. pgd.

`pgomgr /merge test.pgd`

## <a name="see-also"></a>Voir aussi

[Optimisations guidées par profil](profile-guided-optimizations.md)
