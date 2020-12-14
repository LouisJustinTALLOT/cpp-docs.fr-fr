---
description: 'En savoir plus sur : utilisation des bibliothèques d’importation et exportation de fichiers'
title: Utilisation de bibliothèques d'importation et de fichiers d'exportation
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
ms.openlocfilehash: b6e1664aedf5fa87d269e0ff250e6c52d9d18259
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97258796"
---
# <a name="working-with-import-libraries-and-export-files"></a>Utilisation de bibliothèques d'importation et de fichiers d'exportation

Vous pouvez utiliser LIB avec l’option/DEF pour créer une bibliothèque d’importation et un fichier d’exportation. LINK utilise le fichier d’exportation pour créer un programme qui contient des exportations (généralement une bibliothèque de liens dynamiques (DLL)) et utilise la bibliothèque d’importation pour résoudre les références à ces exportations dans d’autres programmes.

Notez que si vous créez votre bibliothèque d’importation à une étape préliminaire, avant de créer votre fichier. dll, vous devez passer le même ensemble de fichiers objets lors de la génération du fichier. dll, comme vous l’avez passé lors de la génération de la bibliothèque d’importation.

Dans la plupart des cas, vous n’avez pas besoin d’utiliser LIB pour créer votre bibliothèque d’importation. Quand vous liez un programme (fichier exécutable ou DLL) qui contient des exportations, LINK crée automatiquement une bibliothèque d’importation qui décrit les exportations. Plus tard, lorsque vous lierez un programme qui référence ces exportations, vous spécifiez la bibliothèque d’importation.

Toutefois, lorsqu’une DLL exporte vers un programme à partir duquel elle importe également, que ce soit directement ou indirectement, vous devez utiliser LIB pour créer l’une des bibliothèques d’importation. Lorsque LIB crée une bibliothèque d’importation, il crée également un fichier d’exportation. Vous devez utiliser le fichier d’exportation lors de la liaison de l’une des dll.

## <a name="see-also"></a>Voir aussi

[Référence LIB](lib-reference.md)
