---
title: /SECTION (EDITBIN)
ms.date: 11/04/2016
f1_keywords:
- /section_editbin
helpviewer_keywords:
- -SECTION editbin option
- SECTION editbin option
- alignment characters in sections
- /SECTION editbin option
ms.assetid: 4680ab4e-c984-4251-8241-93440cad7615
ms.openlocfilehash: 770e1d1c1cf288a7fe68f5bd076791d43f5b8572
ms.sourcegitcommit: 63784729604aaf526de21f6c6b62813882af930a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/17/2020
ms.locfileid: "79438912"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>Notes

Cette option modifie les attributs d’une section, en substituant les attributs qui ont été définis lors de la compilation ou de la liaison du fichier objet pour la section.

Après les deux-points ( **:** ), spécifiez le *nom* de la section. Pour modifier le nom de la section, faites suivre le *nom* d’un signe égal (=) et d’un *NewName* pour la section.

Pour définir ou modifier le `attributes`de la section, spécifiez une virgule ( **,** ) suivie d’un ou plusieurs caractères d’attributs. Pour nier un attribut, faites précéder son caractère d’un point d’exclamation ( !). Les caractères suivants spécifient les attributs de mémoire :

|Attribut|Paramètre|
|---------------|-------------|
|c|code|
|d|pouvant être éliminée|
|e|executable|
|i|données initialisées|
|k|mémoire virtuelle mise en cache|
|m|supprimer un lien|
|o|informations sur le lien|
|p|mémoire virtuelle paginée|
|r|lire|
|s|shared|
|u|données non initialisées|
|w|écrire|

Pour contrôler l' *alignement*, spécifiez le caractère **A** suivi de l’un des caractères suivants pour définir la taille de l’alignement en octets, comme suit :

|Caractère|Taille d’alignement en octets|
|---------------|-----------------------------|
|1|1|
|2|2|
|4|4|
|8|8|
|p|16|
|t|32|
|s|64|
|x|aucun alignement|

Spécifiez les `attributes` et les caractères d' *alignement* sous la forme d’une chaîne sans espace blanc. Les caractères ne respectent pas la casse.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
