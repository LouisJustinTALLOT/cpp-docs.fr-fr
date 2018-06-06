---
title: Mots réservés | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
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
dev_langs:
- C++
helpviewer_keywords:
- .def files [C++], reserved words
- def files [C++], reserved words
- linker [C++], reserved words
- reserved words [C++]
ms.assetid: 9b9f49e5-0739-45ab-a37e-81e3915ceb25
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 132bd8e5ba66cbf9486a6da4747994c667e2f6e7
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705658"
---
# <a name="reserved-words"></a>Mots réservés

Les mots suivants sont réservés par l’éditeur de liens. Ces noms peuvent être utilisés en tant qu’arguments dans [les instructions de définition de module](../../build/reference/module-definition-dot-def-files.md) uniquement si le nom est placé entre guillemets doubles ( » »).

||||
|-|-|-|
|**APPLOADER**<sup>1</sup>|**INITINSTANCE**<sup>2</sup>|**PRÉCHARGEMENT**|
|**BASE**|**IOPL**|**PRIVÉ**|
|**CODE**|**BIBLIOTHÈQUE**<sup>1</sup>|**PROTMODE**<sup>2</sup>|
|**CONFORME**|**LOADONCALL**<sup>1</sup>|**PURE**<sup>1</sup>|
|**DONNÉES**|**LONGNAMES**<sup>2</sup>|**EN LECTURE SEULE**|
|**DESCRIPTION**|**MOBILE**<sup>1</sup>|**LECTURE/ÉCRITURE**|
|**DEV386**|**MOBILE**<sup>1</sup>|**EN MODE RÉEL ;**<sup>1</sup>|
|**POUVANT ÊTRE ÉLIMINÉE**|**PLUSIEURS**|**RÉSIDENT**|
|**DYNAMIQUE**|**NOM**|**RESIDENTNAME**<sup>1</sup>|
|**EXÉCUTER UNIQUEMENT**|**NEWFILES**<sup>2</sup>|**SECTIONS**|
|**EXECUTEONLY**|**NODATA**<sup>1</sup>|**SEGMENTS**|
|**EXÉCUTIONLECTURE**|**NOIOPL**<sup>1</sup>|**PARTAGÉ**|
|**EXETYPE**|**NONAME**|**UNIQUE**|
|**EXPORTS**|**NON CONFORMES**<sup>1</sup>|**STACKSIZE**|
|**FIXE**<sup>1</sup>|**NONDISCARDABLE**|**STUB**|
|**FONCTIONS**<sup>2</sup>|**AUCUN**|**VERSION**|
|**HEAPSIZE**|**NON PARTAGÉ**|**WINDOWAPI**|
|**IMPORTATIONS**|**NOTWINDOWCOMPAT**<sup>1</sup>|**WINDOWCOMPAT**|
|**IMPURES**<sup>1</sup>|**OBJETS**|**WINDOWS**|
|**INCLURE**<sup>2</sup>|**ANCIEN**<sup>1</sup>||

<sup>1</sup> l’éditeur de liens émet un avertissement (« ignoré ») lorsqu’il rencontre ce terme. Toutefois, le mot est toujours réservé.

<sup>2</sup> l’éditeur de liens ignore ce mot mais n’émet aucun avertissement.

## <a name="see-also"></a>Voir aussi

- [Définition des options de l’Éditeur de liens](../../build/reference/setting-linker-options.md)
- [Options de l’éditeur de liens](../../build/reference/linker-options.md)