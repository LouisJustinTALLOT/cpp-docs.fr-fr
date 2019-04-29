---
title: Spécification d'un fichier inline
ms.date: 11/04/2016
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
ms.openlocfilehash: 7eb123ef3f2115df5c65d266630bded8cb54baae
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62318535"
---
# <a name="specifying-an-inline-file"></a>Spécification d'un fichier inline

Spécifier deux crochets pointus (<<) dans la commande où *filename* doit apparaître. Les crochets pointus ne peut pas être une expansion macro.

## <a name="syntax"></a>Syntaxe

```
<<[filename]
```

## <a name="remarks"></a>Notes

Lorsque la commande est exécutée, les crochets pointus sont remplacés par *filename*, s’il est spécifié, ou par un nom unique généré par NMAKE. Si spécifié, *filename* doit suivre les chevrons sans espace ni tabulation. Un chemin d’accès est autorisé. Aucune extension n’est requis ou supposée. Si *filename* est spécifié, le fichier est créé en cours ou le répertoire spécifié, remplaçant les fichiers de ce nom ; sinon, il est créé dans le répertoire TMP (ou le répertoire actuel, si la variable d’environnement TMP non défini). Si une précédente *filename* est réutilisé, NMAKE remplace le fichier précédent.

## <a name="see-also"></a>Voir aussi

[Fichiers inline dans un makefile](inline-files-in-a-makefile.md)
