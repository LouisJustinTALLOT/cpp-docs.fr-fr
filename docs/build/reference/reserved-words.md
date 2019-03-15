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
ms.openlocfilehash: 7d51f599dfb81dfa860e1bdba86c4372e80379fb
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57822442"
---
# <a name="reserved-words"></a>Mots réservés

Les mots suivants sont réservés par l’éditeur de liens. Ces noms peuvent être utilisés en tant qu’arguments dans [les instructions de définition de module](module-definition-dot-def-files.md) uniquement si le nom est placé entre guillemets doubles ( » »).

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**PRÉCHARGEMENT**|
|**BASE DE**|**IOPL**|**PRIVATE**|
|**CODE**|**BIBLIOTHÈQUE**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**CONFORME**|**LOADONCALL**<sup>1</sup>|**PURE**<sup>1</sup>|
|**DATA**|**LONGNAMES**<sup>2</sup>|**EN LECTURE SEULE**|
|**DESCRIPTION**|**MOBILE**<sup>1</sup>|**READWRITE**|
|**DEV386**|**MOVEABLE**<sup>1</sup>|**EN MODE RÉEL ;**<sup>1</sup>|
|**POUVANT ÊTRE ÉLIMINÉE**|**PLUSIEURS**|**RÉSIDENT**|
|**DYNAMIC**|**NOM**|**RESIDENTNAME**<sup>1</sup>|
|**EXÉCUTER UNIQUEMENT**|**NEWFILES**<sup>2</sup>|**SECTIONS**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTS**|
|**EXÉCUTIONLECTURE**|**NOIOPL**<sup>1</sup>|**PARTAGÉ**|
|**EXETYPE**|**NONAME**|**UNIQUE**|
|**EXPORTS**|**NON CONFORMES**<sup>1</sup>|**STACKSIZE**|
|**FIXE**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**FONCTIONS**<sup>2</sup>|**NONE**|**VERSION**|
|**HEAPSIZE**|**NON PARTAGÉ**|**WINDOWAPI**|
|**IMPORTS**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**IMPURES**<sup>1</sup>|**OBJECTS**|**WINDOWS**|
|**INCLUDE**<sup>2</sup>|**OLD**<sup>1</sup>||

<sup>1</sup> l’éditeur de liens émet un avertissement (« ignoré ») lorsqu’il rencontre ce terme. Toutefois, le mot est toujours réservé.

<sup>2</sup> l’éditeur de liens ignore ce mot, mais n’émet aucun avertissement.

## <a name="see-also"></a>Voir aussi

- [Référence de l’éditeur de liens MSVC](linking.md)
- [Options de l’éditeur de liens MSVC](linker-options.md)