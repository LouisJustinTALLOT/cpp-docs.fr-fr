---
title: En spécifiant le chemin d’accès | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.reviewer: ''
ms.suite: ''
ms.technology:
- cpp-tools
ms.tgt_pltfrm: ''
ms.topic: article
dev_langs:
- C++
helpviewer_keywords:
- names [C++], compiler output files
- cl.exe compiler, output files
- output files, specifying pathnames
ms.assetid: 7a6595ce-3383-44ae-957a-466bfa29c343
caps.latest.revision: 6
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: 2412ab15317604e1d6cccc5535226d429d8ba6b7
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="specifying-the-pathname"></a>Spécification du nom de chemin
Chaque option de fichier de sortie accepte un *chemin d’accès* argument peut spécifier un emplacement et un nom pour le fichier de sortie. L’argument peut inclure un nom de lecteur, le répertoire et le nom de fichier. Aucun espace n’est autorisé entre l’option et l’argument.  
  
 Si *chemin d’accès* inclut un nom de fichier sans extension, le compilateur attribue à la sortie une extension par défaut. Si *chemin d’accès* inclut un répertoire, mais aucun nom de fichier, le compilateur crée un fichier avec un nom par défaut dans le répertoire spécifié. Le nom par défaut est basé sur le nom de base du fichier source et une extension par défaut en fonction du type du fichier de sortie. Si vous omettez *chemin d’accès* entièrement, le compilateur crée un fichier avec un nom par défaut dans un répertoire par défaut.  
  
 Vous pouvez également le *chemin d’accès* argument peut être un nom de périphérique (AUX, CON, PRN ou NUL) au lieu d’un nom de fichier. N’utilisez pas d’espace entre l’option et le nom du périphérique ou un signe deux-points dans le cadre du nom du périphérique.  
  
|Nom de l’appareil|Représente|  
|-----------------|----------------|  
|AUX|Dispositif auxiliaire|  
|CON|Console|  
|PRN|Imprimante|  
|NUL|Périphérique NULL (aucun fichier créé)|  
  
## <a name="example"></a>Exemple  
 La ligne de commande suivante envoie un fichier de mappage à l’imprimante :  
  
```  
CL /FmPRN HELLO.CPP  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Fichier de sortie (/ F) Options](../../build/reference/output-file-f-options.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)