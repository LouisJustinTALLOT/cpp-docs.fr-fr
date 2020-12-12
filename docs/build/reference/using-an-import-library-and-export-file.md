---
description: 'En savoir plus sur : utilisation d’une bibliothèque d’importation et d’un fichier d’exportation'
title: Utilisation d'une bibliothèque d'importation et d'un fichier d'exportation
ms.date: 11/04/2016
helpviewer_keywords:
- circular exports
- import libraries, using
- export files
ms.assetid: 2634256a-8aa5-4495-8c9e-6cde10e4ed76
ms.openlocfilehash: f42a98ebe19cb32fb77964f26c37928776b5b30c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97247018"
---
# <a name="using-an-import-library-and-export-file"></a>Utilisation d'une bibliothèque d'importation et d'un fichier d'exportation

Lorsqu’un programme (un fichier exécutable ou une DLL) exporte vers un autre programme à partir duquel il importe également, ou si plus de deux programmes exportent et importent les uns des autres, les commandes pour lier ces programmes doivent prendre en charge les exportations circulaires.

Dans une situation sans exportations circulaires, lorsque vous liez un programme qui utilise des exportations d’un autre programme, vous devez spécifier la bibliothèque d’importation pour le programme d’exportation. La bibliothèque d’importation pour le programme d’exportation est créée lorsque vous liez ce programme d’exportation. Par conséquent, vous devez lier le programme d’exportation avant le programme d’importation. Par exemple, si TWO.dll importations à partir de ONE.dll, vous devez d’abord lier ONE.dll et obtenir la bibliothèque d’importation ONE. lib. Ensuite, vous spécifiez un. lib lors de la liaison de TWO.dll. Lorsque l’éditeur de liens crée TWO.dll, il crée également sa bibliothèque d’importation, TWO. lib. Utilisez TWO. lib lors de la liaison de programmes qui importent à partir de TWO.dll.

Toutefois, dans une situation d’exportation circulaire, il n’est pas possible de lier tous les programmes interdépendants à l’aide des bibliothèques d’importation des autres programmes. Dans l’exemple présenté précédemment, si TWO.dll exporte également vers ONE.dll, la bibliothèque d’importation pour TWO.dll n’existe pas encore quand ONE.dll est lié. Lorsque des exportations circulaires existent, vous devez utiliser LIB pour créer une bibliothèque d’importation et un fichier d’exportation pour l’un des programmes.

Pour commencer, choisissez l’un des programmes sur lesquels exécuter LIB. Dans la commande LIB, listez l’ensemble des objets et des bibliothèques pour le programme et spécifiez/DEF. Si le programme utilise un fichier. def ou des spécifications/EXPORT, spécifiez-les également.

Une fois que vous avez créé la bibliothèque d’importation (. lib) et le fichier d’exportation (. exp) du programme, vous utilisez la bibliothèque d’importation pour lier les autres programmes. LINK crée une bibliothèque d’importation pour chaque programme d’exportation qu’il génère. Par exemple, si vous exécutez LIB sur les objets et les exportations pour ONE.dll, vous créez un. lib et un. exp. Vous pouvez maintenant utiliser un. lib lors de la liaison de TWO.dll ; Cette étape crée également la bibliothèque d’importation TWO. lib.

Enfin, liez le programme que vous avez commencé. Dans la commande de liaison, spécifiez les objets et les bibliothèques pour le programme, le fichier. exp créé pour le programme, ainsi que la ou les bibliothèques d’importation pour les exportations utilisées par le programme. Pour continuer l’exemple, la commande LINK pour ONE.dll contient ONE. exp et TWO. lib, ainsi que les objets et les bibliothèques qui entrent dans ONE.dll. Ne spécifiez pas le fichier. def ou les spécifications/EXPORT dans la commande LINK ; celles-ci ne sont pas nécessaires, car les définitions d’exportation sont contenues dans le fichier. exp. Lorsque vous créez un lien à l’aide d’un fichier. exp, LINK ne crée pas de bibliothèque d’importation, car il suppose qu’un fichier a été créé lors de la création du fichier. exp.

## <a name="see-also"></a>Voir aussi

[Utilisation de bibliothèques d’importation et de fichiers d’exportation](working-with-import-libraries-and-export-files.md)
