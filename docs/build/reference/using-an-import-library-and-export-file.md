---
title: À l’aide d’une bibliothèque d’importation et d’un fichier d’exportation | Microsoft Docs
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
ms.openlocfilehash: 77157ae9404e1d64aec34c897af7564511f275f8
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45717237"
---
# <a name="using-an-import-library-and-export-file"></a>Utilisation d'une bibliothèque d'importation et d'un fichier d'exportation

Lorsqu’un programme (un fichier exécutable ou une DLL) exporte vers un autre programme qu’il importe également à partir de, ou si plus de deux programmes les exportent vers et importer les uns des autres, les commandes pour lier ces programmes doivent prendre en charge les exportations circulaires.

Dans une situation sans exportation circulaire, lors de la liaison d’un programme qui utilise des exportations à partir d’un autre programme, vous devez spécifier la bibliothèque d’importation pour le programme d’exportation. La bibliothèque d’importation pour le programme d’exportation est créée lorsque vous liez ce programme exportateur. Par conséquent, vous devez lier le programme exportateur avant le programme d’importation. Par exemple, si TWO.dll importe à partir de ONE.dll, vous devez d’abord lier ONE.dll et obtenir la bibliothèque d’importation ONE.lib. Ensuite, vous devez spécifier ONE.lib lors de la liaison de TWO.dll. Lorsque l’éditeur de liens crée TWO.dll, il crée également sa bibliothèque d’importation, TWO.lib. Utilisez cette dernière lors de la liaison de programmes qui importent de TWO.dll.

Toutefois, dans une situation d’exportation circulaire, il n’est pas possible de lier tous les programmes interdépendants, à l’aide de bibliothèques d’importation à partir des autres programmes. Dans l’exemple indiqué précédemment, si TWO.dll exporte également vers ONE.dll, la bibliothèque d’importation de TWO.dll n’existe pas encore quand ONE.dll est liée. Lorsque des exportations circulaires existent, vous devez utiliser LIB pour créer une bibliothèque d’importation et exportation de fichier pour l’un des programmes.

Pour commencer, choisissez un des programmes sur lequel exécuter LIB. Dans la commande LIB, répertoriez tous les objets et bibliothèques pour le programme et spécifiez /DEF. Si le programme utilise un fichier .def ou des spécifications /EXPORT, spécifiez-les également.

Après avoir créé la bibliothèque d’importation (.lib) et le fichier d’exportation (.exp) pour le programme, vous utilisez la bibliothèque d’importation lors de la liaison des autres programmes. LINK crée une bibliothèque d’importation pour chaque programme exportateur qu’il génère. Par exemple, si vous exécutez LIB sur les objets et les exportations pour ONE.dll, vous créez ONE.lib et ONE.exp. Vous pouvez désormais utiliser ONE.lib lors de la liaison de TWO.dll ; Cette étape crée également la bibliothèque d’importation TWO.lib.

Enfin, liez le programme que vous avez commencé avec. Dans la commande de lien, spécifiez les objets et les bibliothèques du programme, le fichier .exp que LIB créé pour le programme et la bibliothèque d’importation ou des bibliothèques pour les exportations utilisées par le programme. Pour continuer avec l’exemple, la commande LINK de ONE.dll contient ONE.exp et TWO.lib, ainsi que les objets et les bibliothèques dans ONE.dll. Ne spécifiez pas le fichier .def ou des spécifications /EXPORT dans la commande de lien. celles-ci ne sont pas nécessaires, car les définitions d’exportation sont contenues dans le fichier .exp. Lorsque vous liez à l’aide d’un fichier .exp, LINK ne crée pas une bibliothèque d’importation, parce qu’il suppose que l’une a été créé lorsque le fichier .exp a été créé.

## <a name="see-also"></a>Voir aussi

[Utilisation de bibliothèques d’importation et de fichiers d’exportation](../../build/reference/working-with-import-libraries-and-export-files.md)