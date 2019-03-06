---
title: Dump des importations à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
ms.openlocfilehash: 208be91d9ee873bd181bdb6c7880a6f9032e0d90
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57423948"
---
# <a name="dumping-delay-loaded-imports"></a>Dump des importations à chargement différé

Importations à chargement différé peuvent être vidées à l’aide de [dumpbin /imports](../../build/reference/imports-dumpbin.md) et s’affichent avec des informations légèrement différentes importations standard. Ils sont séparés dans leur propre section de vidage /imports et sont étiquetés explicitement en tant qu’importations à chargement différé. S’il existe de décharger les informations présentes dans l’image, qui est indiquée. S’il existe des informations de liaison présentes, le cachet de date/heure de la DLL cible est indiqué, ainsi que les adresses liées des importations.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les DLL à chargement différé](../../build/reference/linker-support-for-delay-loaded-dlls.md)
