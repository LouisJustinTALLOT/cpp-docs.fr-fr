---
title: -diagnostics (options du compilateur de diagnostic) | Documents Microsoft
ms.custom: 
ms.date: 11/11/2016
ms.reviewer: 
ms.suite: 
ms.technology: cpp-tools
ms.tgt_pltfrm: 
ms.topic: article
f1_keywords:
- /diagnostics
- VC.Project.VCCLCompilerTool.DiagnosticsFormat
dev_langs: C++
helpviewer_keywords:
- /diagnostics compiler diagnostic options [C++]
- -diagnostics compiler diagnostic options [C++]
- diagnostics compiler diagnostic options [C++]
ms.assetid: db1cc175-6e93-4a2e-9396-c3725d2d8f71
caps.latest.revision: "15"
author: corob-msft
ms.author: corob
manager: ghogen
ms.openlocfilehash: 4034e875c2feb52f938edeb4b05383d954476a21
ms.sourcegitcommit: ebec1d449f2bd98aa851667c2bfeb7e27ce657b2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/24/2017
---
# <a name="diagnostics-compiler-diagnostic-options"></a>/Diagnostics (options de diagnostic du compilateur)  
  
Utilisez le **/diagnostics** option du compilateur pour spécifier l’affichage des informations d’emplacement erreur et d’avertissement.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/diagnostics:{caret|classic|column}
```  

## <a name="remarks"></a>Remarques  
Le **/diagnostics** option du compilateur contrôle l’affichage des informations d’erreur et avertissement.  
  
Le **/diagnostics:classic** option est la valeur par défaut, ce qui n'indique que le numéro de ligne où le problème a été trouvé.  
  
Le **/diagnostics:column** option inclut également la colonne où le problème a été trouvé. Cela peut vous aider à identifier la construction de langage spécifique ou un caractère qui pose problème.  
  
Le **/diagnostics:caret** option permet d’inclure la colonne dans laquelle le problème a été trouvé et place le signe insertion (^) sous l’emplacement dans la ligne de code où le problème a été détecté.  
  
Notez que dans certains cas, le compilateur ne détecte pas un problème où il s’est produite. Par exemple, un point-virgule manquant ne pas être détecté tant que symboles autres et inattendues ont été rencontrés. La colonne est signalée et le point d’insertion est placé dans lequel le compilateur a détecté que quelque chose est incorrecte, ce qui n’est pas toujours où vous souhaitez apporter la correction.  
  
Le **/diagnostics** option est disponible à partir de Visual Studio 2017.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1. Ouvrez votre projet **Pages de propriétés** boîte de dialogue.   
  
2. Sous **propriétés de Configuration**, développez le **C/C++** dossier et choisissez le **général** page de propriétés.  
  
3. Utilisez le contrôle de liste déroulante dans le **Diagnostics Format** pour sélectionner un diagnostic vous utilisiez l’option. Choisissez **OK** ou **appliquer** pour enregistrer vos modifications.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)