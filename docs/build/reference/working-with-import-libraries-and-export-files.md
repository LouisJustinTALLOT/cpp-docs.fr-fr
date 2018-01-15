---
title: "Utilisation des bibliothèques d’importation et exportation de fichiers | Documents Microsoft"
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
dev_langs: C++
helpviewer_keywords:
- LIB [C++], /DEF option
- import libraries
- LIB [C++], import libraries and export files
- export files
- import libraries, creating
ms.assetid: d8175596-9773-4c2f-959d-b05b065a5161
caps.latest.revision: "7"
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload: cplusplus
ms.openlocfilehash: 9e0d60eed00abc60c09e03838a113c424d8f173a
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="working-with-import-libraries-and-export-files"></a>Utilisation de bibliothèques d'importation et de fichiers d'exportation
Vous pouvez utiliser LIB avec l’option /DEF pour créer une bibliothèque d’importation et d’un fichier d’exportation. LINK utilise le fichier d’exportation pour générer un programme contenant des exportations (généralement une bibliothèque de liens dynamiques (DLL)), et il utilise la bibliothèque d’importation pour résoudre les références à ces exportations dans d’autres programmes.  
  
 Notez que si vous créez votre bibliothèque d’importation dans une étape préliminaire, avant de créer votre fichier .dll, vous devez passer le même jeu de fichiers objets lors de la génération du fichier .dll que vous avez passé lors de la création de la bibliothèque d’importation.  
  
 Dans la plupart des cas, il est inutile d’utiliser LIB pour créer votre bibliothèque d’importation. Lorsque vous liez un programme (un fichier exécutable ou une DLL) qui contient des exportations, LINK crée automatiquement une bibliothèque d’importation décrivant les exportations. Plus tard, lorsque vous liez un programme qui fait référence à ces exportations, vous spécifiez la bibliothèque d’importation.  
  
 Toutefois, lorsqu’une DLL exporte un programme qui elle importe également à partir de, si directement ou indirectement, vous devez utiliser LIB pour créer une des bibliothèques d’importation. Quand LIB crée une bibliothèque d’importation, il crée également un fichier d’exportation. Vous devez utiliser le fichier d’exportation lors de la liaison d’une des DLL.  
  
## <a name="see-also"></a>Voir aussi  
 [Référence LIB](../../build/reference/lib-reference.md)