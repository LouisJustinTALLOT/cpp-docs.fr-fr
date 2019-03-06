---
title: Fichiers inline multiples
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: 5b41d448c89ac30d891c41d1ad1e314cbf9724a8
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57425612"
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

[Fichiers inline dans un makefile](../build/inline-files-in-a-makefile.md)
