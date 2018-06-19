---
title: Erreur LNK1181 des outils Éditeur de liens | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-diagnostics
ms.topic: error-reference
f1_keywords:
- LNK1181
dev_langs:
- C++
helpviewer_keywords:
- LNK1181
ms.assetid: 984b0db6-e331-4284-b2a7-a212fe96c486
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 617678e5453acdafaf72875857b0e0f9b84a110a
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33301357"
---
# <a name="linker-tools-error-lnk1181"></a>Erreur des outils Éditeur de liens LNK1181
Impossible d’ouvrir le fichier d’entrée 'nom_fichier'  
  
 L’éditeur de liens n’a pas pu trouver `filename` , car il n’existe pas ou le chemin d’accès est introuvable.  
  
 Parmi les causes courantes de l’erreur LNK1181 incluent :  
  
-   `filename` est référencé comme dépendance supplémentaire sur la ligne de l’éditeur de liens, mais le fichier n’existe pas.  
  
-   A **/LIBPATH** instruction qui spécifie le répertoire contenant `filename` est manquant.  
  
 Pour résoudre les problèmes ci-dessus, vérifiez les fichiers référencés sur la ligne de l’éditeur de liens sont présents sur le système.  Également Vérifiez qu’il existe un **/LIBPATH** instruction pour chaque répertoire contenant un fichier dépendant de l’éditeur de liens.  
  
 Autre cause possible de LNK1181 est qu’un nom de fichier long avec des espaces incorporés n’était pas entre guillemets.  Dans ce cas, l’éditeur de liens seulement reconnaît pas un nom de fichier jusqu’au premier espace et puis supposent une extension de fichier. obj.  La solution à cette situation consiste à placer le nom de fichier long (chemin d’accès plus nom de fichier) entre guillemets.  
  
 Pour plus d’informations, consultez [fichiers .lib en tant qu’entrée de l’éditeur de liens](../../build/reference/dot-lib-files-as-linker-input.md).  
  
## <a name="see-also"></a>Voir aussi  
 [/LIBPATH (Autre chemin de bibliothèque)](../../build/reference/libpath-additional-libpath.md)