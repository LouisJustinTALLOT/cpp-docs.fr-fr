---
title: Fichiers Inline multiples | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- inline files, multiple NMAKE
- multiple inline files
- NMAKE program, inline files
ms.assetid: 6d381dcf-0ed8-45d1-8df3-b4598d860b99
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 87d68034c4f0018d65020915d24d0b5c2ec5d61a
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45725593"
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