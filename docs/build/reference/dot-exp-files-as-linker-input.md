---
title: Fichiers .exp en tant qu'entrée de l'Éditeur de liens
ms.date: 11/04/2016
helpviewer_keywords:
- exporting functions
- import libraries, linker files
- linking [C++], exports
- exporting functions, information about exported functions
- exporting data, export (.exp) files
- functions [C++], exporting
- .exp files [C++]
- EXP files
ms.assetid: 399f5636-0a4d-462e-b500-5f5b9ae5ad22
ms.openlocfilehash: 0f2f5c22752d6d938700228fc208c21b8f32cc7b
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293665"
---
# <a name="exp-files-as-linker-input"></a>Fichiers .exp en tant qu'entrée de l'Éditeur de liens

Fichiers d’exportation (.exp) contiennent des informations sur les éléments de données et des fonctions exportées. Quand LIB crée une bibliothèque d’importation, il crée également un fichier .exp. Vous utilisez le fichier .exp lorsque vous liez un programme qui les exporte vers et importe à partir d’un autre programme, directement ou indirectement. Si vous liez un fichier .exp, LINK ne crée pas une bibliothèque d’importation, parce qu’il suppose que LIB déjà créé une. Pour plus d’informations sur les fichiers .exp et les bibliothèques d’importation, consultez [utilisation de bibliothèques d’importation et exportation de fichiers](working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée LINK](link-input-files.md)<br/>
[Options de l’éditeur de liens MSVC](linker-options.md)
