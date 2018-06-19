---
title: -Wp64 (détecter les problèmes de portabilité 64 bits) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- VC.Project.VCCLWCECompilerTool.Detect64BitPortabilityProblems
- VC.Project.VCCLCompilerTool.Detect64BitPortabilityProblems
- /wp64
dev_langs:
- C++
helpviewer_keywords:
- 64-bit compiler [C++], detecting portability problems
- /Wp64 compiler option [C++]
- -Wp64 compiler option [C++]
- Wp64 compiler option [C++]
ms.assetid: 331ae5aa-e627-4d03-8f63-dd2c2d76dadd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 295f2f690cb3c9db17a410cea1f23d04e54b0054
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32379170"
---
# <a name="wp64-detect-64-bit-portability-issues"></a>/Wp64 (Détecter les problèmes de portabilité 64 bits)

L'option du compilateur est obsolète. Dans les versions de Visual studio antérieures à Visual Studio 2013, cette option détecte les problèmes de portabilité 64 bits sur les types qui sont également marqués avec le mot clé [__w64](../../cpp/w64.md) .  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/Wp64  
```  
  
## <a name="remarks"></a>Notes  

Par défaut, dans les versions de Visual Studio antérieures à Visual Studio 2013, le **/Wp64** option du compilateur est désactivée dans le compilateur Visual C++ qui s’appuie 32 bits x86 code, et sur dans le compilateur Visual C++ génère 64 bits, x64 code.  
  
> [!IMPORTANT]
>  L'option de compilateur [/Wp64](../../build/reference/wp64-detect-64-bit-portability-issues.md) et le mot clé [__w64](../../cpp/w64.md) sont déconseillés dans Visual Studio 2010 et Visual Studio 2012 et non pris en charge depuis Visual Studio 2013. Si vous convertissez un projet qui utilise ce commutateur, le commutateur ne sera pas migré lors de la conversion. Pour utiliser cette option dans Visual Studio 2010 ou Visual Studio 2012, vous devez taper le commutateur du compilateur sous **Options supplémentaires** dans la section **Ligne de commande** des propriétés du projet. Si vous utilisez l’option de compilateur **/Wp64** sur la ligne de commande, le compilateur émet l’avertissement de ligne de commande D9002. Au lieu d’utiliser cette option et un mot clé pour détecter les problèmes de portabilité 64 bits, utilisez un compilateur Visual C++ qui cible une plateforme 64 bits et spécifiez l’option [/W4](../../build/reference/compiler-option-warning-level.md) . Pour plus d’informations, consultez [configurer Visual C++ pour 64 bits, x64 cibles](../../build/configuring-programs-for-64-bit-visual-cpp.md).  
  
Les variables des types suivants sont testées sur un système d’exploitation 32 bits comme si elles étaient utilisées sur un système d’exploitation 64 bits :  
  
-   int  
  
-   long  
  
-   pointer  
  
 Si vous compilez régulièrement votre application à l’aide d’un compilateur qui génère les 64 bits, x64 le code, vous pouvez désactiver **/Wp64** dans vos compilations 32 bits, car le compilateur 64 bits détectera tous les problèmes. Pour plus d’informations sur le système d’exploitation de la cible Windows 64 bits, consultez [configurer Visual C++ pour 64 bits, x64 cibles](../../build/configuring-programs-for-64-bit-visual-cpp.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriétés** du projet.  
  
     Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Changez la zone **Options supplémentaires** pour y inclure **/Wp64**.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.Detect64BitPortabilityProblems%2A>.  
  
## <a name="see-also"></a>Voir aussi  

[Options du compilateur](../../build/reference/compiler-options.md)   
[Définition des Options du compilateur](../../build/reference/setting-compiler-options.md)   
[Configurer Visual C++ pour des cibles x64 64 bits](../../build/configuring-programs-for-64-bit-visual-cpp.md)