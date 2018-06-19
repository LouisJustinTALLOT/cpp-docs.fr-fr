---
title: -PROFIL (profileur des outils performances) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCLinkerTool.Profile
dev_langs:
- C++
helpviewer_keywords:
- -PROFILE linker option
- /PROFILE linker option
ms.assetid: e676baa1-5063-47a3-a357-ba0d1f0d1699
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 15379914b4c4852e3065d1abc03c2ce1b17fb044
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32377116"
---
# <a name="profile-performance-tools-profiler"></a>/PROFILE (Profileur des outils d'analyse des performances)
Génère un fichier de sortie utilisable avec le profileur Outils d’analyse des performances.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/PROFILE  
```  
  
## <a name="remarks"></a>Notes  
 /Profile implique les options de l’éditeur de liens suivantes :  
  
-   [/ OPT : REF](../../build/reference/opt-optimizations.md)  
  
-   / OPT : NOICF  
  
-   [/ INCREMENTAL : NO](../../build/reference/incremental-link-incrementally.md)  
  
-   [/ FIXE : NO](../../build/reference/fixed-fixed-base-address.md)  
  
 /Profile indique à l’éditeur de liens générer une section de réadressage dans l’image de programme.  Une section de réadressage permet au profileur de transformer l’image de programme pour obtenir des données de profil.  
  
 **/ PROFIL** n’est disponible uniquement dans les versions entreprise (développement en équipe).  Pour plus d’informations sur PREfast, consultez [analyse du Code pour C/C++ Overview](/visualstudio/code-quality/code-analysis-for-c-cpp-overview).  
  
### <a name="to-set-this-linker-option-in-the-visual-studio-development-environment"></a>Pour définir cette option de l'éditeur de liens dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Développez le **propriétés de Configuration** nœud.  
  
3.  Développez le **l’éditeur de liens** nœud.  
  
4.  Sélectionnez le **avancé** page de propriétés.  
  
5.  Modifier la **profil** propriété.  
  
### <a name="to-set-this-linker-option-programmatically"></a>Pour définir cette option de l'éditeur de liens par programmation  
  
1.  Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.Profile%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Définition des Options de l’éditeur de liens](../../build/reference/setting-linker-options.md)   
 [Options de l’éditeur de liens](../../build/reference/linker-options.md)