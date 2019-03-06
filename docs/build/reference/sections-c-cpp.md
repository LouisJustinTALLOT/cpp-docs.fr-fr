---
title: SECTIONS (C/C++)
ms.date: 11/04/2016
f1_keywords:
- SECTIONS
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
ms.openlocfilehash: d70c8d6e7188844a8721b37d5e80fb88a4e21ef9
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57412794"
---
# <a name="sections-cc"></a>SECTIONS (C/C++)

Introduit une section d’une ou plusieurs `definitions` qui sont des spécificateurs d’accès sur des sections dans le fichier de sortie de votre projet.

```
SECTIONS
definitions
```

## <a name="remarks"></a>Notes

Chaque définition doit être sur une ligne distincte. Le `SECTIONS` mot clé peut être sur la même ligne que la première définition ou sur une ligne précédente. Le fichier .def peut contenir une ou plusieurs `SECTIONS` instructions.

Cela `SECTIONS` instruction définit les attributs d’une ou plusieurs sections dans le fichier image et peut être utilisée pour remplacer les attributs par défaut pour chaque type de section.

Le format de `definitions` est :

`.section_name specifier`

où `.section_name` est le nom d’une section dans l’image de votre programme et `specifier` est une ou plusieurs des modificateurs d’accès suivants :

|Modificateur|Description|
|--------------|-----------------|
|`EXECUTE`|La section est exécutable.|
|`READ`|Permet les opérations de lecture sur les données|
|`SHARED`|Partage la section entre tous les processus qui chargent l’image|
|`WRITE`|Autorise les opérations d’écriture sur les données|

Séparez les noms de spécificateur par un espace. Exemple :

```
SECTIONS
.rdata READ WRITE
```

`SECTIONS` marque le début d’une liste de section `definitions`. Chaque `definition` doit se trouver sur une ligne distincte. Le `SECTIONS` mot clé peut se trouver sur la même ligne que le premier `definition` ou sur une ligne précédente. Le fichier .def peut contenir une ou plusieurs `SECTIONS` instructions. Le `SEGMENTS` mot clé est prise en charge comme synonyme de `SECTIONS`.

Versions antérieures de Visual C++ prenaient en charge :

```
section [CLASS 'classname'] specifier
```

Le `CLASS` mot clé est prise en charge pour la compatibilité, mais il est ignoré.

Méthode équivalente pour spécifier les attributs de section est avec la [/SECTION](../../build/reference/section-specify-section-attributes.md) option.

## <a name="see-also"></a>Voir aussi

[Règles s’appliquant aux instructions de définition de module](../../build/reference/rules-for-module-definition-statements.md)
