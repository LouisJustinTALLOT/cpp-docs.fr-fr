---
title: 'Génération de fichiers d’informations : Vue d’ensemble de | Documents Microsoft'
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- .bsc files, about .bsc files
- bsc files, about bsc files
- browse information files (.bsc)
- browse information files (.bsc), creating
ms.assetid: b5c12832-51f6-4953-8044-4264dd0fb242
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 463bf72c07c775ef0d4965a2023e5699cf7ec715
ms.sourcegitcommit: b04de4e90def1d0f4aa265e96d6b73779d010e1f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/07/2018
ms.locfileid: "34843073"
---
# <a name="building-browse-information-files-overview"></a>Génération de fichiers d'informations de consultation : vue d'ensemble
Pour créer des informations de consultation de symboles, le compilateur crée un fichier .sbr pour chaque fichier source dans votre projet, puis BSCMAKE. EXE concatène les fichiers .sbr dans un fichier .bsc.  
  
 Génération de fichiers .sbr et .bsc prend un certain temps, Visual C++ désactive ces fonctions par défaut. Si vous souhaitez parcourir les données en cours, vous devez activer les options de navigation et régénérer votre projet.  
  
 Utilisez [/FR](../../build/reference/fr-fr-create-dot-sbr-file.md) ou [/Fr](../../build/reference/fr-fr-create-dot-sbr-file.md) pour indiquer au compilateur de créer des fichiers .sbr. Pour créer les fichiers .bsc, vous pouvez appeler [BSCMAKE](../../build/reference/bscmake-command-line.md) à partir de la ligne de commande. En utilisant BSCMAKE depuis la ligne de commande vous donne un contrôle plus précis sur la manipulation de fichiers d’informations. Consultez [référence BSCMAKE](../../build/reference/bscmake-reference.md) pour plus d’informations.  
  
> [!TIP]
>  Vous pouvez activer la génération du fichier .sbr mais laisser la génération du fichier .bsc mises hors tension. Cela vous bénéficierez vous permet également de créer un fichier .bsc actualisé rapidement par la génération du fichier .bsc sous tension et la génération du projet.  
  
 Vous pouvez réduire le temps, la mémoire et espace disque requis pour générer un fichier .bsc en réduisant la taille du fichier .bsc.  
  
 Consultez [général, Page de propriétés (projet)](../../ide/general-property-page-project.md) pour plus d’informations sur la façon de générer un fichier browser dans l’environnement de développement.  
  
### <a name="to-create-a-smaller-bsc-file"></a>Pour créer un fichier .bsc plus petit  
  
1.  Utilisez [les options de ligne de commande BSCMAKE](../../build/reference/bscmake-options.md) pour exclure les informations à partir du fichier d’informations.  
  
2.  Omettre les symboles locaux dans un ou plusieurs fichiers .sbr lors de la compilation ou l’assemblage.  
  
3.  Si un fichier objet ne contient pas les informations nécessaires pour la phase en cours de débogage, omettez son fichier .sbr dans la commande BSCMAKE lorsque vous régénérez le fichier d’informations.  
  
### <a name="to-combine-the-browse-information-from-several-projects-into-one-browser-file-bsc"></a>Pour combiner les informations de consultation à partir de plusieurs projets dans un fichier browser (.bsc)  
  
1.  Ne pas créer le fichier .bsc au niveau du projet ou utiliser le commutateur /n pour empêcher que les fichiers .sbr tronqués.  
  
2.  Une fois que tous les projets sont générés, exécutez BSCMAKE avec tous les fichiers .sbr en tant qu’entrée. Les caractères génériques sont acceptés. Par exemple, si vous aviez des répertoires de projet C:\X, C:\Y et C:\Z des fichiers .sbr que vous souhaitez combiner en un fichier .bsc, puis utilisez BSCMAKE C:\X\\\*.sbr C:\Y\\\*.sbr C:\Z\\ \*.sbr /o c:\whatever_directory\combined.bsc pour générer le fichier .bsc combiné.  
  
## <a name="see-also"></a>Voir aussi  
 [Outils de génération C/C++](../../build/reference/c-cpp-build-tools.md)   
 [Référence BSCMAKE](../../build/reference/bscmake-reference.md)
