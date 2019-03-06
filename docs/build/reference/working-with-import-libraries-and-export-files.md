---
title: Utilisation de bibliothèques d'importation et de fichiers d'exportation
ms.date: 11/04/2016
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
ms.openlocfilehash: fa759482d6949b27f5076643d83e92cddc1d8fac
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57416564"
---
# <a name="working-with-import-libraries-and-export-files"></a>Utilisation de bibliothèques d'importation et de fichiers d'exportation

Vous pouvez utiliser LIB avec l’option /DEF pour créer une bibliothèque d’importation et d’un fichier d’exportation. LINK utilise le fichier d’exportation pour générer un programme qui contienne des exportations (généralement une bibliothèque de liens dynamiques (DLL)), et il utilise la bibliothèque d’importation pour résoudre les références à ces exportations dans d’autres programmes.

Notez que si vous créez votre bibliothèque d’importation dans une étape préliminaire, avant de créer votre fichier .dll, vous devez passer le même ensemble de fichiers objets lors de la génération du fichier .dll que vous avez passé lors de la création de la bibliothèque d’importation.

Dans la plupart des cas, il est inutile d’utiliser LIB pour créer votre bibliothèque d’importation. Lorsque vous liez un programme (un fichier exécutable ou une DLL) qui contient des exportations, LINK crée automatiquement une bibliothèque d’importation décrivant les exportations. Plus tard, lorsque vous liez un programme qui fait référence à ces exportations, vous spécifiez la bibliothèque d’importation.

Toutefois, quand une DLL exporte vers un programme qu’il importe également à partir de, si directement ou indirectement, vous devez utiliser LIB pour créer une des bibliothèques d’importation. Quand LIB crée une bibliothèque d’importation, il crée également un fichier d’exportation. Vous devez utiliser le fichier d’exportation lors de la liaison d’une des DLL.

## <a name="see-also"></a>Voir aussi

[Référence LIB](../../build/reference/lib-reference.md)
