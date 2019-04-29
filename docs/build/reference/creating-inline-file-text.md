---
title: Création du texte d'un fichier inline
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
ms.openlocfilehash: a45aa526ca99af93cda86a2a8e0580d4d036ca6d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62272319"
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

[Fichiers inline dans un makefile](inline-files-in-a-makefile.md)
