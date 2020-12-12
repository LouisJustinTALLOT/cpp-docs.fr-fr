---
description: 'En savoir plus sur : SECTIONS (C/C++)'
title: SECTIONS (C/C++)
ms.date: 11/04/2016
f1_keywords:
- SECTIONS
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
ms.openlocfilehash: aaebeb19c921dfb389c55209c7a371f49043cb56
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224762"
---
# <a name="sections-cc"></a>SECTIONS (C/C++)

Introduit une section d’un ou plusieurs `definitions` spécificateurs d’accès sur les sections du fichier de sortie de votre projet.

```
SECTIONS
definitions
```

## <a name="remarks"></a>Notes

Chaque définition doit être sur une ligne distincte. Le `SECTIONS` mot clé peut se trouver sur la même ligne que la première définition ou sur une ligne précédente. Le fichier. def peut contenir une ou plusieurs `SECTIONS` instructions.

Cette `SECTIONS` instruction définit les attributs d’une ou plusieurs sections du fichier image et peut être utilisée pour remplacer les attributs par défaut pour chaque type de section.

Le format de `definitions` est le suivant :

`.section_name specifier`

où `.section_name` est le nom d’une section dans votre image de programme et `specifier` un ou plusieurs des modificateurs d’accès suivants :

|Modificateur|Description|
|--------------|-----------------|
|`EXECUTE`|La section est exécutable|
|`READ`|Autorise les opérations de lecture sur les données|
|`SHARED`|Partage la section entre tous les processus qui chargent l’image|
|`WRITE`|Autorise les opérations d’écriture sur les données|

Séparez les noms de spécificateurs par un espace. Par exemple :

```
SECTIONS
.rdata READ WRITE
```

`SECTIONS` marque le début d’une liste de sections `definitions` . Chaque `definition` doit se trouver sur une ligne distincte. Le `SECTIONS` mot clé peut être sur la même ligne que la première `definition` ou sur une ligne précédente. Le fichier. def peut contenir une ou plusieurs `SECTIONS` instructions. Le `SEGMENTS` mot clé est pris en charge comme synonyme de `SECTIONS` .

Les versions antérieures de Visual C++ prises en charge :

```
section [CLASS 'classname'] specifier
```

Le `CLASS` mot clé est pris en charge pour la compatibilité, mais il est ignoré.

Une méthode équivalente pour spécifier des attributs de section est avec l’option [/section](section-specify-section-attributes.md) .

## <a name="see-also"></a>Voir aussi

[Règles pour les instructions Module-Definition](rules-for-module-definition-statements.md)
