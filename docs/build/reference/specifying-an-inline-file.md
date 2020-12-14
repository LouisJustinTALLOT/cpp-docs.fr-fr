---
description: 'En savoir plus sur : spécification d’un fichier Inline'
title: Spécification d'un fichier inline
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
ms.openlocfilehash: 461bf507f707512aa690e81dc5752a97d0c1c4ce
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224606"
---
# <a name="specifying-an-inline-file"></a>Spécification d'un fichier inline

Spécifiez deux crochets angulaires (<<) dans la commande où *filename* doit apparaître. Les chevrons ne peuvent pas être une expansion macro.

## <a name="syntax"></a>Syntaxe

```
<<[filename]
```

## <a name="remarks"></a>Notes

Lorsque la commande est exécutée, les crochets pointus sont remplacés par un nom de *fichier*, s’il est spécifié ou par un nom unique généré par NMAKE. S’il est spécifié, le *nom de fichier* doit suivre les chevrons sans espace ou tabulation. Un chemin d’accès est autorisé. Aucune extension n’est requise ou supposée. Si *filename* est spécifié, le fichier est créé dans le répertoire actif ou spécifié, remplaçant tout fichier existant par ce nom ; dans le cas contraire, il est créé dans le répertoire TMP (ou le répertoire actif, si la variable d’environnement TMP n’est pas définie). Si un *nom de fichier* précédent est réutilisé, NMAKE remplace le fichier précédent.

## <a name="see-also"></a>Voir aussi

[Fichiers inline dans un Makefile](inline-files-in-a-makefile.md)
