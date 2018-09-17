---
title: SECTIONS (C/C++) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- SECTIONS
dev_langs:
- C++
helpviewer_keywords:
- SECTIONS .def file statement
ms.assetid: 7b974366-9ef5-4e57-bbcc-73a1df6f8857
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: ecd8d6050df7a4d30b0a37cad28e030d1cd63cf0
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45722892"
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