---
title: -GA (optimiser pour une Application Windows) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLCompilerTool.OptimizeForWindowsApplication
- /ga
dev_langs:
- C++
helpviewer_keywords:
- /GA compiler option [C++]
- GA compiler option [C++]
- -GA compiler option [C++]
- Optimize for Windows compiler options
ms.assetid: be97323e-15a0-4836-862c-95980b51926a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 387732c5bde04970e3a467ca4f43f911afa7a9a6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32374256"
---
# <a name="ga-optimize-for-windows-application"></a>/GA (Optimiser pour une application Windows)
Résultats dans le code plus efficace pour un fichier .exe pour accéder aux variables du stockage local des threads (TLS).  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/GA  
```  
  
## <a name="remarks"></a>Notes  
 **/GA** accélère l’accès aux données déclarées avec [__declspec (thread)](../../cpp/declspec.md) dans un programme basé sur Windows. Lorsque cette option est définie, le [__tls_index a la valeur](http://msdn.microsoft.com/library/windows/desktop/ms686749) macro par défaut est 0.  
  
 À l’aide de **/GA** pour une DLL peut entraîner la génération de code incorrect.  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l'option de compilateur dans la zone **Options supplémentaires** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)