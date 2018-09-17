---
title: . Fichiers exp en tant qu’entrée de l’éditeur de liens | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
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
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 4badc93f38d5ce76dcc294ad4ae216c8e3f6454c
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724007"
---
# <a name="exp-files-as-linker-input"></a>Fichiers .exp en tant qu'entrée de l'Éditeur de liens

Fichiers d’exportation (.exp) contiennent des informations sur les éléments de données et des fonctions exportées. Quand LIB crée une bibliothèque d’importation, il crée également un fichier .exp. Vous utilisez le fichier .exp lorsque vous liez un programme qui les exporte vers et importe à partir d’un autre programme, directement ou indirectement. Si vous liez un fichier .exp, LINK ne crée pas une bibliothèque d’importation, parce qu’il suppose que LIB déjà créé une. Pour plus d’informations sur les fichiers .exp et les bibliothèques d’importation, consultez [utilisation de bibliothèques d’importation et exportation de fichiers](../../build/reference/working-with-import-libraries-and-export-files.md).

## <a name="see-also"></a>Voir aussi

[Fichiers d’entrée LINK](../../build/reference/link-input-files.md)<br/>
[Options de l’éditeur de liens](../../build/reference/linker-options.md)