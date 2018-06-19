---
title: -/QIfist (Supprimer _ftol) | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /qifist
dev_langs:
- C++
helpviewer_keywords:
- QIfist compiler option [C++]
- -QIfist compiler option [C++]
- /QIfist compiler option [C++]
ms.assetid: 1afd32a5-f658-4b66-85f4-e0ce4cb955bd
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 77ec65e330cebb1de718330ba129e960383b31c6
ms.sourcegitcommit: be2a7679c2bd80968204dee03d13ca961eaa31ff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/03/2018
ms.locfileid: "32378403"
---
# <a name="qifist-suppress-ftol"></a>/QIfist (Supprimer _ftol)
Obsolète. Supprime l'appel de la fonction d'assistance `_ftol` quand la conversion d'un type à virgule flottante vers un type intégral est requise.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
/QIfist  
```  
  
## <a name="remarks"></a>Notes  
  
> [!NOTE]
>  **/QIfist** est disponible uniquement dans le compilateur ciblant x86 ; cette option du compilateur n’est pas disponible dans les compilateurs qui ciblent [!INCLUDE[vcprx64](../../assembler/inline/includes/vcprx64_md.md)] orARM.  
  
 Outre la conversion d’un type à virgule flottante en type intégral, la `_ftol` fonction assure le mode d’arrondi de l’unité à virgule flottante (FPU) à zéro (troncature), en définissant les bits 10 et 11 du mot de commande. Cela garantit la conversion d’un type à virgule flottante vers un type intégral se produit comme décrit par la norme C ANSI (la partie fractionnaire du nombre est supprimée). Lorsque vous utilisez **/QIfist**, cette garantie ne s’applique plus. Le mode d’arrondi sera un des quatre comme décrit dans les manuels de référence Intel :  
  
-   Arrondi vers le plus proche (nombre pair si équidistant)  
  
-   Arrondi vers l’infini négatif  
  
-   Arrondi vers l’infini positif  
  
-   Arrondi à zéro  
  
 Vous pouvez utiliser la [_control87, _controlfp, \__control87_2](../../c-runtime-library/reference/control87-controlfp-control87-2.md) fonction C Run-Time pour modifier le comportement d’arrondi de la FPU. La valeur par défaut le mode du FPU d’arrondi est « Arrondi vers le plus proche ». À l’aide de **/QIfist** peut améliorer les performances de votre application, mais non sans risque. Vous devez tester minutieusement les parties de votre code qui sont sensibles aux modes d’arrondi avant de vous fier au code généré avec **/QIfist** dans les environnements de production.  
  
 [/ arch (x86)](../../build/reference/arch-x86.md) et **/QIfist** ne peuvent pas être utilisés sur le même compiland.  
  
> [!NOTE]
>  **/QIfist** est appliqué par défaut, car les bits d’arrondi affectent à virgule flottante flottante également pointe pas arrondi (ce qui se produit après chaque calcul), donc lorsque vous définissez les indicateurs de l’arrondi de style C (à zéro), votre à virgule flottante calculs peuvent être différents. **/QIfist** ne doit pas être utilisé si votre code dépend du comportement attendu de tronquer la partie fractionnaire du nombre à virgule flottante. Si vous ne savez pas, n’utilisez pas **/QIfist**.  
  
 Le **/QIfist** option est déconseillée à compter de Visual Studio 2005. Le compilateur a apporté des améliorations significatives dans float à la vitesse de conversion de type int. Pour obtenir la liste des options du compilateur déconseillées, consultez **déconseillées et supprimées des Options du compilateur** dans [Options du compilateur classées par catégorie](../../build/reference/compiler-options-listed-by-category.md).  
  
### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio  
  
1.  Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [utilisation des propriétés de projet](../../ide/working-with-project-properties.md).  
  
2.  Cliquez sur le dossier **C/C++** .  
  
3.  Cliquez sur la page de propriétés **Ligne de commande** .  
  
4.  Tapez l'option de compilateur dans la zone **Options supplémentaires** .  
  
### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation  
  
-   Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.  
  
## <a name="see-also"></a>Voir aussi  
 [/Q (opérations de bas niveau), options](../../build/reference/q-options-low-level-operations.md)   
 [Options du compilateur](../../build/reference/compiler-options.md)   
 [Définition des options du compilateur](../../build/reference/setting-compiler-options.md)