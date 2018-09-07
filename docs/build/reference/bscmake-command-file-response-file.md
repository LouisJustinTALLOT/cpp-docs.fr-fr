---
title: BSCMAKE, fichier de commandes (fichier réponse) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, response file
- BSCMAKE, command file
- response files, BSCMAKE
- command files, BSCMAKE
- response files
- command files
ms.assetid: abdffeea-35c7-4f2d-8c17-7d0d80bac314
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 2a14e0ba315820eec0dd2fe17823f2c5c656fd87
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43895108"
---
# <a name="bscmake-command-file-response-file"></a>BSCMAKE, fichier de commandes (fichier réponse)

Vous pouvez fournir tout ou partie de l’entrée de ligne de commande dans un fichier de commandes. Spécifiez le fichier de commandes à l’aide de la syntaxe suivante :

```  
BSCMAKE @filename
```  

Fichier de commandes qu’un seul est autorisé. Vous pouvez spécifier un chemin d’accès avec *filename*. Faites précéder *filename* avec un arobase (**\@**). BSCMAKE n’assume pas une extension. Vous pouvez spécifier supplémentaires *sbrfiles* sur la ligne de commande après *filename*. Le fichier de commandes est un fichier texte qui contient l’entrée à BSCMAKE dans le même ordre que vous le définiriez sur la ligne de commande. Séparez les arguments de ligne de commande avec un ou plusieurs espaces, des tabulations ou des caractères de saut de ligne.

La commande suivante appelle BSCMAKE à l’aide d’un fichier de commandes :

```  
BSCMAKE @prog1.txt
```  

Voici un exemple de fichier de commande :

```  
/n /v /o main.bsc /El
/S (  
toolbox.h
verdate.h c:\src\inc\screen.h
)
file1.sbr file2.sbr file3.sbr file4.sbr
```  

## <a name="see-also"></a>Voir aussi

[Référence BSCMAKE](../../build/reference/bscmake-reference.md)