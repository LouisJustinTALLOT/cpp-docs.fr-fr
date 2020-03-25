---
title: Mots réservés
ms.date: 11/04/2016
f1_keywords:
- code
- CONFORMING
- DISCARDABLE
- Description
- base
- APPLOADER
- Data
- DYNAMIC
- DEV386
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
ms.openlocfilehash: 16caacb77e052eebc8e2cd101990ee373535bd6e
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80171149"
---
# <a name="reserved-words"></a>Mots réservés

Les mots suivants sont réservés par l’éditeur de liens. Ces noms peuvent être utilisés comme arguments dans les [instructions de définition de module](module-definition-dot-def-files.md) uniquement si le nom est placé entre guillemets doubles ("").

||||
|-|-|-|
|**Apploader**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**PRÉ**|
|**BASE**|**IOPL**|**PRIV**|
|**CODE**|**Bibliothèque**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**CONFORME**|**LOADONCALL**<sup>1</sup>|**Pur**<sup>1</sup>|
|**MÉTADONNÉE**|**LONGNAMES**<sup>2</sup>|**SEULEMENT**|
|**DESCRIPTION**|**Mobile**<sup>1</sup>|**READWRITE**|
|**DEV386**|**Mobile**<sup>1</sup>|**Realmode**<sup>1</sup>|
|**POUVANT être éliminée**|**PLUSIEURS**|**CEUX**|
|**DYNAMIQUE**|**NAME**|**RESIDENTNAME**<sup>1</sup>|
|**EXÉCUTION SEULE**|**Fichier NewFiles**<sup>2</sup>|**SECTIONS**|
|**EXECUTEONLY**|**NoData**<sup>1</sup>|**SEGMENTS**|
|**EXECUTEREAD**|**NOIOPL**<sup>1</sup>|**PARTAGÉ**|
|**EXETYPE**|**NONAME**|**SINGLE**|
|**EXPORTS**|**Non conforme**<sup>1</sup>|**STACKSIZE**|
|**Fixe**<sup>1</sup>|**Impossible à ignorer**|**STUB**|
|**Fonctions**<sup>2</sup>|**NONE**|**VERSION**|
|**HEAPSIZE**|**NON partagée**|**WINDOWAPI**|
|**TOUTE**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**IMpures**<sup>1</sup>|**OBJETS**|**WINDOWS**|
|**Inclure**<sup>2</sup>|**Ancien**<sup>1</sup>||

<sup>1</sup> l’éditeur de liens émet un avertissement (« ignoré ») lorsqu’il rencontre ce terme. Toutefois, le mot est toujours réservé.

<sup>2</sup> l’éditeur de liens ignore ce mot mais n’émet aucun avertissement.

## <a name="see-also"></a>Voir aussi

- [Informations de référence sur l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)
