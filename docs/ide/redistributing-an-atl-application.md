---
title: Redistribution d’une application ATL | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
dev_langs:
- C++
helpviewer_keywords:
- ATL, redistributing
- redistributing ATL
- redistributing OLE DB templates
- OLE DB templates, redistributing
ms.assetid: 9a696b22-2345-43ec-826b-be7cb8cfd676
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 5c824dd4ae174a4418c6744e592dd62dc54b9595
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
---
# <a name="redistributing-an-atl-application"></a>Redistribution d'une application ATL
À compter de Visual Studio 2012, la bibliothèque ATL (Active Template Library) est une bibliothèque à en-tête uniquement. Les projets ATL ne possèdent pas d'option Lien dynamique vers ATL. Aucun composant redistribuable de bibliothèque ATL n'est requis.  
  
 Si vous redistribuez une application ATL exécutable, vous devez inscrire le fichier .exe (et tous les contrôles qu'il contient) en émettant la commande suivante :  
  
```  
filename /regserver  
```  
  
 où `filename` est le nom du fichier exécutable.  
  
 Dans Visual Studio 2010, un projet ATL peut être généré pour une configuration MinDependency ou MinSize. Une configuration MinDependency est le résultat obtenu lorsque vous définissez la **utilisation des ATL** propriété **lien statique vers ATL** sur la **général** page de propriétés et affectez le  **Bibliothèque Runtime** propriété **multithread (/ MT)** sur la **génération de Code** page de propriétés (dossier C/C++).  
  
 Une configuration MinSize est le résultat obtenu lorsque vous définissez la **utilisation des ATL** propriété **lien dynamique vers ATL** sur la **général** page de propriétés, ou ensemble la **Runtime Bibliothèque** propriété **DLL multithread (/ MD)** sur la **génération de Code** page de propriétés (dossier C/C++).  
  
 MinSize rend la sortie fichier aussi petit que possible, mais requiert que ATL100.dll et Msvcr100.dll (si vous avez sélectionné le **DLL multithread (/ MD)** option) se trouvent sur l’ordinateur cible. Le fichier ATL100.dll doit être inscrit sur l'ordinateur cible pour garantir la présence de toutes les fonctionnalités ATL seront présentes. ATL100.dll contient des exports ANSI et Unicode.  
  
 Si vous générez votre projet de modèles ATL ou OLE DB pour une cible MinDependency, il est inutile d'installer et d'inscrire ATL100.dll sur l'ordinateur cible, bien que vous puissiez obtenir une image de programme plus grande.  
  
 Si vous redistribuez une application ATL exécutable, vous devez inscrire le fichier .exe (et tous les contrôles qu'il contient) en émettant la commande suivante :  
  
```  
filename /regserver  
```  
  
 où `filename` est le nom du fichier exécutable.  
  
 Pour les applications de modèles OLE DB, assurez-vous que l'ordinateur cible dispose des dernières versions des fichiers Microsoft Data Access Components (MDAC). Pour plus d’informations, consultez [redistribution de fichiers de prise en charge de base de données](../ide/redistributing-database-support-files.md).  
  
## <a name="see-also"></a>Voir aussi  
 [Redistribution des fichiers Visual C++](../ide/redistributing-visual-cpp-files.md)