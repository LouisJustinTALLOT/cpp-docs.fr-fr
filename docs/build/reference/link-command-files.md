---
title: Fichiers de commandes LINK | Documents Microsoft
ms.custom: 
ms.date: 11/04/2016
ms.reviewer: 
ms.suite: 
ms.technology:
- cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- link
dev_langs:
- C++
helpviewer_keywords:
- syntax, LINK command files
- command files [C++]
- LINK tool [C++]
- text files, passing arguments to LINK
- LINK tool [C++], command-line syntax
- command files [C++], LINK
ms.assetid: 7154511c-32b9-4e5b-a515-3922fa9de48e
caps.latest.revision: 
author: corob-msft
ms.author: corob
manager: ghogen
ms.workload:
- cplusplus
ms.openlocfilehash: e585fb8fa11d4e3ffe8eff842baacb05f109754c
ms.sourcegitcommit: 8fa8fdf0fbb4f57950f1e8f4f9b81b4d39ec7d7a
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/21/2017
---
# <a name="link-command-files"></a>Fichiers de commandes LINK
Vous pouvez passer des arguments de ligne de commande pour le lien sous la forme d’un fichier de commandes. Pour spécifier un fichier de commandes pour l’éditeur de liens, utilisez la syntaxe suivante :  
  
```  
LINK @commandfile  
```  
  
 Le `commandfile` est le nom d’un fichier texte. Aucun espace ou une tabulation n’est autorisée entre le signe arobase (@) et le nom de fichier. Il n’existe aucune extension par défaut ; Vous devez spécifier le nom de fichier complet, y compris toute extension. Impossible d’utiliser des caractères génériques. Vous pouvez spécifier un chemin d’accès absolu ou relatif avec le nom de fichier. LIEN n’utilise pas une variable d’environnement pour rechercher le fichier.  
  
 Dans le fichier de commandes, les arguments peuvent être séparés par des espaces ou des tabulations (comme la ligne de commande) et par les caractères de saut de ligne.  
  
 Vous pouvez spécifier tout ou partie de la ligne de commande dans un fichier de commandes. Vous pouvez utiliser plusieurs fichiers de commandes dans une commande LINK. LINK accepte l’entrée de fichier de commandes comme si elle était spécifiée à cet emplacement sur la ligne de commande. Fichiers de commandes ne peuvent pas être imbriquées. LIEN renvoie le contenu des fichiers de commandes, à moins que le [/NOLOGO](../../build/reference/nologo-suppress-startup-banner-linker.md) option est spécifiée.  
  
## <a name="example"></a>Exemple  
 La commande suivante pour générer une DLL passe les noms des fichiers objets et bibliothèques dans les fichiers de commandes séparés et utilise un troisième fichier de commandes pour la spécification de l’option /EXPORTS :  
  
```  
link /dll @objlist.txt @liblist.txt @exports.txt  
```  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)