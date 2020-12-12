---
description: En savoir plus sur:/SECTION (EDITBIN)
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
ms.openlocfilehash: 51d1305ca4f3e0e8222ae9408b44563a4c480d57
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224866"
---
# <a name="section-editbin"></a>/SECTION (EDITBIN)

```
/SECTION:name[=newname][,attributes][alignment]
```

## <a name="remarks"></a>Notes

Cette option modifie les attributs d’une section, en substituant les attributs qui ont été définis lors de la compilation ou de la liaison du fichier objet pour la section.

Après les deux-points ( **:** ), spécifiez le *nom* de la section. Pour modifier le nom de la section, faites suivre le *nom* d’un signe égal (=) et d’un *NewName* pour la section.

Pour définir ou modifier la section `attributes` , spécifiez une virgule (**,**) suivie d’un ou de plusieurs caractères d’attributs. Pour nier un attribut, faites précéder son caractère d’un point d’exclamation ( !). Les caractères suivants spécifient les attributs de mémoire :

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
|s|partagés|
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

Spécifiez les `attributes` caractères d' *alignement* et en tant que chaîne sans espace blanc. Les caractères ne respectent pas la casse.

## <a name="see-also"></a>Voir aussi

[Options EDITBIN](editbin-options.md)
