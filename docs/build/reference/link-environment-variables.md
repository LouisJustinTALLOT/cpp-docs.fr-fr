---
title: Variables d’environnement lien | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- variables, environment
- LINK tool [C++], environment variables
- LIB environment variable
- environment variables [C++], LINK
ms.assetid: 9a3d3291-0cc4-4a7d-9d50-80e351b90708
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 076e427e50520651f30cde20c764ff1124a6f953
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32372696"
---
# <a name="link-environment-variables"></a>Variables d'environnement de LINK

L'outil LINK utilise les variables d'environnement suivantes :  
  
-   LIEN et \_lien\_, s’il est défini. L’outil LINK ajoute les options et les arguments définis dans la variable d’environnement LINK, puis ajoute les options et les arguments définis dans le \_lien\_ variable d’environnement pour les arguments de ligne de commande avant le traitement.  
  
-   LIB, si elle est définie. L’outil LINK utilise le chemin d’accès LIB quand vous recherchez un objet, bibliothèque ou un autre fichier spécifié sur la ligne de commande ou par le [/BASE](../../build/reference/base-base-address.md) option. Il utilise également le chemin d’accès LIB pour rechercher un fichier .pdb nommé dans un objet. La variable LIB peut contenir une ou plusieurs spécifications de chemin d'accès, séparées par des points-virgules. Un chemin d'accès doit pointer vers le sous-répertoire \lib de votre installation Visual C++.  
  
-   PATH, si l'outil doit exécuter CVTRES et ne peut pas trouver le fichier dans le même répertoire que LINK. (LINK requiert CVTRES pour lier un fichier .res.) PATH doit pointer vers le sous-répertoire \bin de votre installation Visual C++.  
  
-   TMP, pour spécifier un répertoire lors de la liaison de fichiers OMF ou .res.  
  
## <a name="see-also"></a>Voir aussi  

[Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
[Options de l’éditeur de liens](../../build/reference/linker-options.md)   
[Générer du code C/C++ sur la ligne de commande](../../build/building-on-the-command-line.md)  
[Définir le chemin et les variables d’environnement pour les générations sur la ligne de commande](../../build/setting-the-path-and-environment-variables-for-command-line-builds.md)
