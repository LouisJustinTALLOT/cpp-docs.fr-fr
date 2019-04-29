---
title: Fichiers inline multiples
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: 71f17ff6717e717693facb21b4a4341a040b14c1
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62320589"
---
# <a name="multiple-inline-files"></a>Fichiers inline multiples

Une commande peut créer plusieurs fichiers inline.

## <a name="syntax"></a>Syntaxe

```
command << <<
inlinetext
<<[KEEP | NOKEEP]
inlinetext
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Notes

Pour chaque fichier, spécifiez une ou plusieurs lignes de texte inline suivie d’une ligne de fin contenant le délimiteur. Commencer le deuxième texte du fichier sur la ligne qui suit la ligne de délimitation pour le premier fichier.

## <a name="see-also"></a>Voir aussi

[Fichiers inline dans un makefile](inline-files-in-a-makefile.md)
