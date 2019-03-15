---
title: Dump des importations à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
ms.openlocfilehash: 368c6b851340dd2a39df9a758f15d52ff5104479
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57809910"
---
# <a name="dumping-delay-loaded-imports"></a>Dump des importations à chargement différé

Importations à chargement différé peuvent être vidées à l’aide de [dumpbin /imports](imports-dumpbin.md) et s’affichent avec des informations légèrement différentes importations standard. Ils sont séparés dans leur propre section de vidage /imports et sont étiquetés explicitement en tant qu’importations à chargement différé. S’il existe de décharger les informations présentes dans l’image, qui est indiquée. S’il existe des informations de liaison présentes, le cachet de date/heure de la DLL cible est indiqué, ainsi que les adresses liées des importations.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](linker-support-for-delay-loaded-dlls.md)
