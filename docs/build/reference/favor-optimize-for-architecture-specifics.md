---
title: -favor (optimiser pour les particularités d’Architecture) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /favor
dev_langs:
- C++
helpviewer_keywords:
- -favor compiler option [C++]
- /favor compiler option [C++]
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 91f91373eef29adcb9a632e80520ed6713d3e39b
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32376219"
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor (optimisation pour les particularités d'architecture)
**/ favor :** `option` génère le code qui est optimisé pour une architecture spécifique ou pour les caractéristiques des micro-architectures dans l’AMD et les architectures Intel.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/favor:{blend | ATOM | AMD64 | INTEL64}  
```  
  
## <a name="remarks"></a>Notes  
 **/favor:Blend**  
 (x86 et x64) produit le code qui est optimisé pour les caractéristiques des micro-architectures dans l’AMD et les architectures Intel. Alors que **/favor:blend** ne peut pas fournir les meilleures performances possibles sur un processeur spécifique, il est conçu pour fournir les meilleures performances sur un large éventail de processeurs x86 et x64. Par défaut, **/favor:blend** est en vigueur.  
  
 **/favor:Atom**  
 (x86 et x64) produit le code qui est optimisé pour les caractéristiques du processeur Intel Atom et la technologie processeur Intel Centrino Atom. Code qui est généré à l’aide de **/favor:ATOM** peut également produire des instructions Intel SSSE3, SSE3, SSE2 et SSE pour les processeurs Intel.  
  
 **/favor:AMD64**  
 (x64 uniquement) optimise le code généré pour l’AMD Opteron et les processeurs Athlon qui prennent en charge les extensions 64 bits. Le code optimisé peut s’exécuter sur x64 toutes les plateformes compatibles avec. Code qui est généré à l’aide de **/favor:AMD64** risque de dégradation des performances sur les processeurs Intel qui prennent en charge Intel64.  
  
 **/favor:INTEL64**  
 (x64 uniquement) optimise le code généré pour les processeurs Intel qui prennent en charge Intel64, ce qui entraîne généralement de meilleures performances pour cette plateforme. Le code résultant peut s’exécuter sur n’importe quel x64 plateforme. Code qui est généré avec **/favor:INTEL64** peut entraîner une dégradation des performances sur AMD Opteron et Athlon processeurs qui prennent en charge les extensions 64 bits.  
  
> [!NOTE]
>  Architecture Intel64 était précédemment appelée Extended Memory 64 Technology et l’option du compilateur correspondante a été **/favor:EM64T**.  
  
 Pour plus d’informations sur la programmation pour le [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] architecture, consultez [x64 Conventions des logiciels](../../build/x64-software-conventions.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Sélectionnez le **C/C++** dossier.  
  
3.  Sélectionnez le **ligne de commande** page de propriétés.  
  
4.  Entrez l’option du compilateur dans le **des Options supplémentaires** boîte.  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)