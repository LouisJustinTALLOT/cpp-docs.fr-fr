---
title: Création du texte d’un fichier Inline | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ce0a345c6c2f48d3d5c2e6fb9d9cfc2a5c03e4ed
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45720913"
---
# <a name="creating-inline-file-text"></a>Création du texte d'un fichier inline

Fichiers inline sont temporaire ou permanent.

## <a name="syntax"></a>Syntaxe

```
inlinetext
.
.
.
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Notes

Spécifiez *inlinetext* sur la première ligne après la commande. Marquer la fin avec des doubles crochets pointus (<<) au début d’une ligne distincte. Le fichier contient tous les *inlinetext* avant les crochets de délimitation. Le *inlinetext* peut avoir des expansions macro et substitutions, mais pas les directives ou des commentaires de makefile. Les espaces, les tabulations et les caractères de saut de ligne sont traités littéralement.

Un fichier temporaire existe pendant la durée de la session et peut être réutilisé par d’autres commandes. Spécifiez **conserver** après les crochets de fermeture pour conserver le fichier après la session NMAKE ; un fichier sans nom est conservé sur le disque avec le nom de fichier généré. Spécifiez **NOKEEP** ou rien pour un fichier temporaire. **CONSERVER** et **NOKEEP** ne respectent pas la casse.

## <a name="see-also"></a>Voir aussi

[Fichiers inline dans un makefile](../build/inline-files-in-a-makefile.md)