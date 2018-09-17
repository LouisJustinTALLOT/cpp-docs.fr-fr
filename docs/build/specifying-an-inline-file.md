---
title: Spécification d’un fichier Inline | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- NMAKE program, inline files
- inline files [C++], specifying NMAKE
- files [C++], inline
ms.assetid: 393eccfb-3fc9-4bac-a30c-8ac8d221cca3
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 73983094f10088920100b4fbbb8d870aee13f05e
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720562"
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

[Fichiers inline dans un makefile](../build/inline-files-in-a-makefile.md)