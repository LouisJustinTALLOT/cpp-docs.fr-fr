---
title: -REBASE | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /rebase
dev_langs:
- C++
helpviewer_keywords:
- base addresses [C++]
- -REBASE editbin option
- REBASE editbin option
- DLLs [C++], linking
- executable files [C++], base address
- /REBASE editbin option [C++]
ms.assetid: 3f89d874-af5c-485b-974b-fd205f6e1a4b
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 686306316e6950ba62ea7c44522b95f4d935be0b
ms.sourcegitcommit: 9a0905c03a73c904014ec9fd3d6e59e4fa7813cd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/29/2018
ms.locfileid: "43216172"
---
# <a name="rebase"></a>/REBASE
```  
/REBASE[:modifiers]  
```  
  
## <a name="remarks"></a>Notes  
 Cette option définit les adresses de base pour les fichiers spécifiés. EDITBIN assigne de nouvelles adresses de base dans un espace d’adressage contigu selon la taille de chaque fichier arrondie à 64 Ko les plus proche. Pour plus d’informations sur les adresses de base, consultez le [adresse de Base](../../build/reference/base-base-address.md) (/ BASE) option de l’éditeur de liens.  
  
 Spécifiez les fichiers exécutables du programme et les DLL dans le *fichiers* argument sur la ligne de commande EDITBIN dans l’ordre dans lequel ils doivent être basée. Vous pouvez éventuellement spécifier un ou plusieurs *modificateurs*, chacun étant séparé par une virgule (**,**) :  
  
|Modificateur|Action|  
|--------------|------------|  
|**BASE =**<em>adresse</em>|Fournit une adresse de début pour la réaffectation d’adresses de base pour les fichiers. Spécifiez *adresse* dans la notation décimale ou en langage C. Si la BASE n’est pas spécifiée, l’adresse de base de démarrage par défaut est 0 x 400000. Si bas est utilisé, BASE doit être spécifié, et *adresse* définit la fin de la plage d’adresses de base.|  
|**BASEFILE**|Crée un fichier nommé COFFBASE. TXT, qui est un fichier texte au format attendu par du lien/option de BASE.|  
|**VERS LE BAS**|Indique à EDITBIN de réassigner les adresses de base vers le bas à partir d’une adresse de fin. Les fichiers sont réaffectés dans l’ordre spécifié, avec le premier fichier situé dans l’adresse la plus élevée possible ci-dessous la fin de la plage d’adresses. BASE doit être utilisée avec vers le bas pour vous assurer d’espace d’adressage suffisant pour baser les fichiers. Pour déterminer l’espace d’adressage requis par les fichiers spécifiés, exécutez EDITBIN avec /REBASE sur les fichiers et ajoutez 64 Ko à la taille totale affichée.|  
  
## <a name="see-also"></a>Voir aussi  
 [Options EDITBIN](../../build/reference/editbin-options.md)