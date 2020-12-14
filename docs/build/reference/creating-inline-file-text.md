---
description: 'En savoir plus sur : création d’un texte de fichier Inline'
title: Création du texte d'un fichier inline
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, creating text
- NMAKE program, inline files
- text, inline file
ms.assetid: b8a332ed-8244-4ff8-89e6-029d7f659725
ms.openlocfilehash: 849273fff4ca0853e4589a38096cbb067c380aae
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97196852"
---
# <a name="creating-inline-file-text"></a>Création du texte d'un fichier inline

Les fichiers Inline sont temporaires ou permanents.

## <a name="syntax"></a>Syntaxe

```
inlinetext
.
.
.
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Notes

Spécifiez *inlinetext* sur la première ligne après la commande. Marquer la fin par un double Chevron (<<) au début d’une ligne distincte. Le fichier contient tous les *inlinetext* avant les crochets de délimitation. Le *inlinetext* peut comporter des expansions et des substitutions de macros, mais pas de directives ou de commentaires de Makefile. Les espaces, les tabulations et les caractères de saut de ligne sont traités littéralement.

Un fichier temporaire existe pour la durée de la session et peut être réutilisé par d’autres commandes. Spécifier **Keep** après les chevrons fermants pour conserver le fichier après la session NMAKE ; un fichier sans nom est conservé sur le disque avec le nom de fichier généré. Spécifiez **nokeep** ou Nothing pour un fichier temporaire. **Keep** et **nokeep** ne respectent pas la casse.

## <a name="see-also"></a>Voir aussi

[Fichiers inline dans un Makefile](inline-files-in-a-makefile.md)
