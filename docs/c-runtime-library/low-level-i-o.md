---
title: E/S de bas niveau | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-standard-libraries
ms.topic: conceptual
f1_keywords:
- c.io
dev_langs:
- C++
helpviewer_keywords:
- I/O [CRT], low-level
- I/O [CRT], functions
- low-level I/O routines
- file handles [C++]
- file handles [C++], I/O functions
ms.assetid: 53e11bdd-6720-481c-8b2b-3a3a569ed534
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 34ce75fa9670f28079774f4ba564657d0b4614ac
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32391280"
---
# <a name="low-level-io"></a>E/S niveau bas

Ces fonctions appellent le système d’exploitation directement pour l’opération du niveau inférieur à celui fourni par les E/S de flux. Les appels de bas niveau et de sortie ne mettent pas les données en mémoire tampon et ne les formatent pas.

 Les routines de bas niveau peuvent accéder aux flux standard ouverts au démarrage du programme à l’aide des descripteurs de fichier prédéfinis suivants.

|Flux de données|Descripteur de fichier|
|------------|---------------------|
|**stdin**|0|
|**stdout**|1|
|**stderr**|2|

 Les routines d’E/S de bas niveau définissent la variable globale [errno](../c-runtime-library/errno-doserrno-sys-errlist-and-sys-nerr.md) lorsqu’une erreur se produit. Lorsque vous utilisez des fonctions de bas niveau, vous ne devez inclure STDIO.H que si votre programme nécessite une constante définie dans STDIO.H, comme l’indicateur de fin de fichier (**EOF**).

## <a name="low-level-io-functions"></a>Fonctions d’E/S de bas niveau

|Fonction|Utilisez|
|--------------|---------|
|[_close](../c-runtime-library/reference/close.md)|Fermer le fichier|
|[_commit](../c-runtime-library/reference/commit.md)|Vider le fichier sur disque|
|[_creat, _wcreat](../c-runtime-library/reference/creat-wcreat.md)|Créer le fichier|
|[_dup](../c-runtime-library/reference/dup-dup2.md)|Retourne le descripteur de fichier disponible suivant pour le fichier donné|
|[_dup2](../c-runtime-library/reference/dup-dup2.md)|Créer le deuxième descripteur pour le fichier donné|
|[_eof](../c-runtime-library/reference/eof.md)|Vérifier la fin du fichier|
|[_lseek, _lseeki64](../c-runtime-library/reference/lseek-lseeki64.md)|Repositionner le pointeur de fichier vers un emplacement donné|
|[_open, _wopen](../c-runtime-library/reference/open-wopen.md)|Ouvrir un fichier|
|[_read](../c-runtime-library/reference/read.md)|Lire des données depuis le fichier|
|[_sopen, _wsopen](../c-runtime-library/reference/sopen-wsopen.md), [_sopen_s, _wsopen_s](../c-runtime-library/reference/sopen-s-wsopen-s.md)|Ouvrir le fichier pour le partage de fichiers|
|[_tell, _telli64](../c-runtime-library/reference/tell-telli64.md)|Obtenir la position actuelle du pointeur de fichier|
|[_umask](../c-runtime-library/reference/umask.md), [_umask_s](../c-runtime-library/reference/umask-s.md)|Définir le masque file-permission|
|[_write](../c-runtime-library/reference/write.md)|Écrire les données dans le fichier|

 **_dup** et **_dup2** servent généralement à associer les descripteurs de fichier prédéfinis à différents fichiers.

## <a name="see-also"></a>Voir aussi

[Entrée et sortie](../c-runtime-library/input-and-output.md)<br/>
 [Routines du runtime C universel par catégorie](../c-runtime-library/run-time-routines-by-category.md)<br/>
 [Appels système](../c-runtime-library/system-calls.md)<br/>
