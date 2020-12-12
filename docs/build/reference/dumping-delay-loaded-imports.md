---
description: 'En savoir plus sur : vidage des importations Delay-Loaded'
title: Dump des importations à chargement différé
ms.date: 11/04/2016
helpviewer_keywords:
- delay-loaded imports, dumping
- imports (delay-loaded)
- delay-loaded imports
ms.assetid: f766acf4-9df8-4b85-8cf6-0be3ffc4c124
ms.openlocfilehash: c57ff6bb4a3dce16b4cb1eb85fdffff4ef272396
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97201077"
---
# <a name="dumping-delay-loaded-imports"></a>Dump des importations à chargement différé

Les importations à chargement différé peuvent être vidées à l’aide de [DUMPBIN/Imports](imports-dumpbin.md) et s’afficher avec des informations légèrement différentes de celles des importations standard. Ils sont séparés dans leur propre section du vidage/Imports et sont explicitement étiquetés comme des importations à chargement différé. Si des informations de déchargement sont présentes dans l’image, cela est indiqué. Si des informations de liaison sont présentes, l’horodatage de la DLL cible est noté avec les adresses liées des importations.

## <a name="see-also"></a>Voir aussi

[Prise en charge de l’éditeur de liens pour les dll Delay-Loaded](linker-support-for-delay-loaded-dlls.md)
