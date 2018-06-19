---
title: Définir le chemin d’accès et les Variables d’environnement pour les versions de ligne de commande | Documents Microsoft
ms.custom: conceptual
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: conceptual
f1_keywords:
- include
- Lib
- Path
dev_langs:
- C++
helpviewer_keywords:
- environment variables [C++]
- VCVARS32.bat file
- cl.exe compiler [C++], environment variables
- LINK tool [C++], environment variables
- PATH reserved word
- INCLUDE reserved word
- LINK tool [C++], path
- LIB environment variable
- compiling source code [C++], from command line
- environment variables [C++], CL compiler
ms.assetid: 99389528-deb5-43b9-b99a-03c8773ebaf4
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 0b72f13fe25330b81a48d1447b707bdc4626ab3f
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32381133"
---
# <a name="set-the-path-and-environment-variables-for-command-line-builds"></a>Définir le chemin d’accès et les Variables d’environnement pour les versions de ligne de commande

Les outils de génération de ligne de commande de Visual C++ requièrent plusieurs variables d’environnement qui sont personnalisés pour votre configuration de l’installation et de la build. Lorsqu’une charge de travail C++ est installée à la [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] programme d’installation, il crée des fichiers de commande personnalisé ou des fichiers de commandes, définissez les variables d’environnement requises. Le programme d’installation utilise ensuite ces fichiers de commandes pour créer des raccourcis du menu Démarrer de Windows ouvrir une fenêtre d’invite de commandes développeur. Ces raccourcis configurer les variables d’environnement pour un spécifiques à une configuration de build. Lorsque vous souhaitez utiliser les outils de ligne de commande, vous pouvez exécuter un de ces raccourcis, ou vous pouvez ouvrir une fenêtre d’invite de commande simple et puis exécutez un des fichiers de commande personnalisée pour définir l’environnement de configuration de build vous-même. Pour plus d’informations, consultez [générer le Code C/C++ sur la ligne de commande](building-on-the-command-line.md).  
  
Les outils de ligne de commande Visual C++ utilisent les variables d’environnement PATH, TMP, INCLUDE, LIB et LIBPATH et également utilisent des variables d’environnement spécifiques à vos outils installés, les plateformes et les kits de développement logiciel. Même une simple [!INCLUDE[vsprvs](../assembler/masm/includes/vsprvs_md.md)] installation peut définir des variables d’environnement vingt ou plus. Étant donné que les valeurs de ces variables d’environnement sont spécifiques à votre installation et de configuration de build de votre choix et peuvent être modifiés par les mises à jour de produit ou des mises à niveau, nous recommandons que vous utilisez un raccourci d’invite de commandes développeur ou l’un de le fichiers de commandes personnalisé pour les définir, au lieu de les définir dans l’environnement Windows vous-même. 

Pour afficher les variables d’environnement sont définies par un raccourci d’invite de commandes développeur, vous pouvez utiliser la commande SET. Ouvrez une fenêtre d’invite de commandes ordinaire et capturer la sortie de la commande SET pour une ligne de base. Ouvrez une fenêtre d’invite de commandes développeur et capturer la sortie de la commande SET pour la comparaison. Un outil de comparaison tels que celui de l’IDE de Visual Studio peut être utile pour comparer les variables d’environnement et de voir ce qui est défini par l’invite de commandes développeur. Pour plus d’informations sur les variables d’environnement spécifiques utilisés par le compilateur et l’éditeur de liens, consultez [Variables d’environnement CL](../build/reference/cl-environment-variables.md) et [Variables d’environnement lien](../build/reference/link-environment-variables.md).  
  
> [!NOTE]
>  Plusieurs outils de ligne de commande ou les options de l’outil peuvent nécessiter une autorisation d’administrateur. Si vous avez des problèmes d’autorisation lorsque vous les utilisez, nous vous recommandons d’ouvrir la fenêtre d’invite de commandes développeur à l’aide de la **exécuter en tant qu’administrateur** option. Sur Windows 10, avec le bouton droit pour ouvrir le menu contextuel de la fenêtre d’invite de commandes, puis choisissez **plus**, **exécuter en tant qu’administrateur**.  
  
## <a name="see-also"></a>Voir aussi  

[Générer du code C/C++ sur la ligne de commande](../build/building-on-the-command-line.md)   
[Liaison](../build/reference/linking.md)   
[Options de l’éditeur de liens](../build/reference/linker-options.md)   
[Compilation d’un programme C/C++](../build/reference/compiling-a-c-cpp-program.md)   
[Options du compilateur](../build/reference/compiler-options.md)