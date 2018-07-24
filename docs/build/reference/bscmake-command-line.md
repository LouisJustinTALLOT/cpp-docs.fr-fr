---
title: Ligne de commande BSCMAKE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
dev_langs:
- C++
helpviewer_keywords:
- BSCMAKE, command line
ms.assetid: 8006e8cf-8bfe-4c23-868a-b0a25e6bbf0f
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: b79f7e7c181112877c795f3601e8211e70403563
ms.sourcegitcommit: 7eadb968405bcb92ffa505e3ad8ac73483e59685
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/23/2018
ms.locfileid: "39207745"
---
# <a name="bscmake-command-line"></a>Ligne de commande BSCMAKE
Pour exécuter BSCMAKE, utilisez la syntaxe de ligne de commande suivante :  
  
```  
BSCMAKE [options] sbrfiles  
```  
  
 Options peuvent apparaître uniquement dans le `options` champ sur la ligne de commande.  
  
 Le *sbrfiles* champ spécifie un ou plusieurs fichiers .sbr créés par un compilateur ou un assembleur. Séparez les noms des fichiers .sbr avec des espaces ou des tabulations. Vous devez spécifier l’extension. Il n’existe aucune valeur par défaut. Vous pouvez spécifier un chemin d’accès avec le nom de fichier, et vous pouvez utiliser des caractères génériques de système d’exploitation (\* et ?).  
  
 Pendant une génération incrémentielle, vous pouvez spécifier de nouveaux fichiers .sbr qui ne faisaient pas partie de la génération d’origine. Si vous souhaitez que toutes les contributions à rester dans le fichier d’informations de consultation, vous devez spécifier tous les fichiers .sbr (y compris les fichiers tronqués) qui ont servi à créer le fichier .bsc. Si vous omettez un fichier .sbr, la contribution de ce fichier pour le fichier d’informations est supprimée.  
  
 Ne spécifiez pas un fichier .sbr tronqué pour une génération complète. Une génération complète nécessite la contribution de tous les fichiers .sbr spécifié. Avant d’effectuer une génération complète, recompilez le projet et créez un fichier .sbr pour chaque fichier vide.  
  
 La commande suivante exécute BSCMAKE pour générer un fichier nommé MAIN.bsc à partir de trois fichiers .sbr :  
  
```  
BSCMAKE main.sbr file1.sbr file2.sbr  
```  
  
 Pour plus d’informations, consultez [BSCMAKE, fichier de commandes](../../build/reference/bscmake-command-file-response-file.md) et [Options BSCMAKE](../../build/reference/bscmake-options.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Référence BSCMAKE](../../build/reference/bscmake-reference.md)