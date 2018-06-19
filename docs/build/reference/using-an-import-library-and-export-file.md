---
title: À l’aide d’une bibliothèque d’importation et d’un fichier d’exportation | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 946ef702d17762e6771bad206d0bfa682a61055e
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378595"
---
# <a name="using-an-import-library-and-export-file"></a>Utilisation d'une bibliothèque d'importation et d'un fichier d'exportation
Lorsqu’un programme (un fichier exécutable ou une DLL) exporte vers un autre programme qu’il importe également à partir de, ou si plusieurs programmes les exportent vers et importer les uns des autres, les commandes pour lier ces programmes doivent tenir compte des exportations circulaires.  
  
 Dans une situation sans exportation circulaire, lors de la liaison d’un programme qui utilise des exportations à partir d’un autre programme, vous devez spécifier la bibliothèque d’importation pour le programme d’exportation. La bibliothèque d’importation pour le programme d’exportation est créée lorsque vous liez ce programme exportateur. Par conséquent, vous devez lier le programme exportateur avant le programme d’importation. Par exemple, si TWO.dll importe à partir de ONE.dll, vous devez d’abord lier ONE.dll et obtenir la bibliothèque d’importation ONE.lib. Ensuite, vous spécifiez ONE.lib lorsque vous liez TWO.dll. Lorsque l’éditeur de liens crée TWO.dll, il crée également sa bibliothèque d’importation, TWO.lib. Utilisez cette dernière lors de la liaison des programmes qui importent de TWO.dll.  
  
 Toutefois, dans une situation d’exportation circulaire, il n’est pas possible de lier tous les programmes interdépendants, à l’aide des bibliothèques d’importation à partir d’autres programmes. Dans l’exemple indiqué précédemment, si TWO.dll exporte également vers ONE.dll, la bibliothèque d’importation de TWO.dll n’existera pas encore quand ONE.dll sera lié. Lorsque les exportations circulaires existent, vous devez utiliser LIB pour créer une bibliothèque d’importation et exportation de fichier pour l’un des programmes.  
  
 Pour commencer, choisissez un des programmes sur lequel exécuter LIB. Dans la commande LIB, répertorier tous les objets et les bibliothèques du programme et spécifiez /DEF. Si le programme utilise un fichier .def ou des spécifications/Export, spécifiez-les également.  
  
 Après avoir créé la bibliothèque d’importation (.lib) et le fichier d’exportation (.exp) pour le programme, vous utilisez la bibliothèque d’importation lors de la liaison des autres programmes. LINK crée une bibliothèque d’importation pour chaque programme exportateur qu’il génère. Par exemple, si vous exécutez LIB sur les objets et les exportations pour ONE.dll, vous créez ONE.lib et ONE.exp. Vous pouvez désormais utiliser ONE.lib lors de la liaison de TWO.dll ; Cette étape crée également la bibliothèque d’importation TWO.lib.  
  
 Enfin, liez le programme que vous avez commencé avec. Dans la commande LINK, spécifiez les objets et les bibliothèques du programme, le fichier .exp que LIB a créé pour le programme et que la bibliothèque d’importation ou bibliothèques pour les exportations utilisées par le programme. Pour continuer avec l’exemple, la commande LINK de ONE.dll contient ONE.exp et TWO.lib, ainsi que les objets et les bibliothèques dans ONE.dll. Ne spécifiez pas le fichier .def ou des spécifications /EXPORT dans la commande LINK ; celles-ci ne sont pas nécessaires, car les définitions d’exportation sont contenues dans le fichier .exp. Lorsque vous liez un fichier .exp, LINK ne crée pas une bibliothèque d’importation, car il suppose que l’un a été créé lors de la création du fichier .exp.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de bibliothèques d’importation et de fichiers d’exportation](../../build/reference/working-with-import-libraries-and-export-files.md)