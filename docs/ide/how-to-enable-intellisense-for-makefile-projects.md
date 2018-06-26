---
title: Guide pratique pour activer IntelliSense pour des projets Makefile | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-ide
ms.topic: conceptual
f1_keywords:
- VC.Project.VCNMakeTool.IntelliSense
dev_langs:
- C++
helpviewer_keywords:
- Makefile projects, IntelliSense
- IntelliSense, Makefile projects
ms.assetid: 9443f453-f18f-4f12-a9a1-ef9dbf8b188f
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: 4b9b11f04f1fe8d201d6d07ca5ed83f9ca7d991b
ms.sourcegitcommit: a4454b91d556a3dc43d8755cdcdeabcc9285a20e
ms.translationtype: HT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/04/2018
ms.locfileid: "34705460"
---
# <a name="how-to-enable-intellisense-for-makefile-projects"></a>Comment : activer IntelliSense pour des projets Makefile
IntelliSense ne fonctionne pas dans l’IDE de projets Makefile Visual C++ quand des paramètres de projet, ou options du compilateur, sont incorrectement configurés. Utilisez cette procédure pour configurer les projets Makefile Visual C++ afin qu’IntelliSense fonctionne quand ces projets sont ouverts dans l’environnement de développement Visual Studio.  
  
### <a name="to-enable-intellisense-for-makefile-projects-in-the-ide"></a>Pour activer IntelliSense pour des projets Makefile dans l’IDE  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés**. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../ide/working-with-project-properties.md).  
  
2.  Développez le nœud **Propriétés de configuration**.  
  
3.  Sélectionnez la page de propriétés **NMake**, puis modifiez les propriétés figurant sous **IntelliSense** à votre convenance.  
  
    -   Définissez la propriété **Définitions de préprocesseur** pour définir n’importe quel symbole de préprocesseur dans votre projet Makefile. Pour plus d’informations, consultez [/D (Définitions de préprocesseur)](../build/reference/d-preprocessor-definitions.md).  
  
    -   Définissez la propriété **Chemin de recherche Include** de façon à spécifier la liste des répertoires dans lesquels le compilateur effectue ses recherches afin de résoudre les références de fichier passées aux directives de préprocesseur dans votre projet Makefile. Pour plus d’informations, consultez [/I (Autres répertoires Include)](../build/reference/i-additional-include-directories.md).  
  
         Pour les projets qui sont générés à l’aide de CL.EXE depuis une fenêtre Commande, définissez la variable d’environnement **INCLUDE** de façon à spécifier les répertoires dans lesquels le compilateur effectue ses recherches afin de résoudre les références de fichier passées aux directives de préprocesseur dans votre projet Makefile.  
  
    -   Définissez la propriété **Fichiers Include forcés** pour spécifier les fichiers d’en-tête à traiter lors de la génération de votre projet Makefile. Pour plus d’informations, consultez [/FI (Nom du fichier Include imposé)](../build/reference/fi-name-forced-include-file.md).  
  
    -   Définissez la propriété **Chemin de recherche des assemblys** pour spécifier la liste des répertoires dans lesquels le compilateur effectue ses recherches afin de résoudre les références aux assemblys .NET dans votre projet. Pour plus d’informations, consultez [/AI (Spécifier les répertoires des métadonnées)](../build/reference/ai-specify-metadata-directories.md).  
  
    -   Définissez la propriété **Utilisation forcée des assemblys** pour spécifier les assemblys .NET à traiter lors de la génération de votre projet Makefile. Pour plus d’informations, consultez [/FU (Nom du fichier #using imposé)](../build/reference/fu-name-forced-hash-using-file.md).  
  
    -   Définissez la propriété **Options supplémentaires** de façon à spécifier les commutateurs du compilateur supplémentaires que doit utiliser IntelliSense lors de l’analyse de fichiers C++.  
  
4.  Cliquez sur **OK** pour fermer les pages de propriétés.  
  
5.  Utilisez la commande **Enregistrer tout** pour enregistrer les paramètres modifiés du projet.  
  
 La prochaine fois que vous ouvrez votre projet Makefile dans l’environnement de développement Visual Studio, exécutez les commandes **Nettoyer la solution**, puis **Générer la solution** sur votre projet Makefile. IntelliSense doit fonctionner correctement dans l’IDE.  
  
## <a name="see-also"></a>Voir aussi  
 [Utilisation de la fonctionnalité IntelliSense](/visualstudio/ide/using-intellisense)   
 [Référence NMAKE](../build/nmake-reference.md)   
 [Guide pratique pour créer un projet C++ à partir d’un code existant](../ide/how-to-create-a-cpp-project-from-existing-code.md)