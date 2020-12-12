---
description: 'En savoir plus sur : plusieurs fichiers Inline'
title: Fichiers inline multiples
ms.date: 11/04/2016
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
ms.openlocfilehash: d739591910007f69eca5d4834f6943ae0a0082ed
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97190599"
---
# <a name="multiple-inline-files"></a>Fichiers inline multiples

Une commande peut créer plusieurs fichiers Inline.

## <a name="syntax"></a>Syntaxe

```
command << <<
inlinetext
<<[KEEP | NOKEEP]
inlinetext
<<[KEEP | NOKEEP]
```

## <a name="remarks"></a>Notes

Pour chaque fichier, spécifiez une ou plusieurs lignes de texte inclus suivies d’une ligne de fermeture contenant le délimiteur. Commencez le texte du deuxième fichier sur la ligne qui suit la ligne de délimitation pour le premier fichier.

## <a name="see-also"></a>Voir aussi

[Fichiers inline dans un Makefile](inline-files-in-a-makefile.md)
