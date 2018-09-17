---
title: -favoriser (optimiser pour les particularités d’Architecture) | Microsoft Docs
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
ms.openlocfilehash: 03d1bdce12e461446f1804844040457dae6e9d43
ms.sourcegitcommit: 92f2fff4ce77387b57a4546de1bd4bd464fb51b6
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/17/2018
ms.locfileid: "45724754"
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor (optimisation pour les particularités d'architecture)

**/ favor :** `option` génère le code qui est optimisé pour une architecture spécifique ou pour les caractéristiques des micro-architectures dans le AMD et les architectures Intel.

## <a name="syntax"></a>Syntaxe

```
/favor:{blend | ATOM | AMD64 | INTEL64}
```

## <a name="remarks"></a>Notes

**/favor:Blend**<br/>
(x86 et x64) génère le code qui est optimisé pour les caractéristiques des micro-architectures dans le AMD et les architectures Intel. Bien que **/favor:blend** peut ne pas donner les meilleures performances possibles sur un processeur spécifique, il est conçu pour fournir les meilleures performances sur une large gamme de processeurs x86 et x64. Par défaut, **/favor:blend** est en vigueur.

**/favor:Atom**<br/>
(x86 et x64) génère le code qui est optimisé pour les caractéristiques du processeur Intel Atom et technologie de processeur Intel Centrino Atom. Code généré à l’aide de **/favor:ATOM** peut également entraîner des instructions Intel SSSE3, SSE3, SSE2 et SSE pour les processeurs Intel.

**/favor:AMD64**<br/>
(x64 uniquement) optimise le code généré pour l’AMD Opteron et les processeurs Athlon qui prennent en charge des extensions 64 bits. Le code optimisé peut s’exécuter sur x64 toutes les plateformes compatibles. Code généré à l’aide de **/favor:AMD64** peut entraîner de dégradation des performances sur les processeurs Intel qui prennent en charge Intel64.

**/favor:INTEL64**<br/>
(x64 uniquement) optimise le code généré pour les processeurs Intel qui prennent en charge Intel64, ce qui entraîne généralement de meilleures performances pour cette plateforme. Le code résultant peut s’exécuter sur n’importe quel x64 plateforme. Code qui est généré avec **/favor:INTEL64** peut entraîner une dégradation des performances sur AMD Opteron et Athlon processeurs qui prennent en charge des extensions 64 bits.

> [!NOTE]
> Intel64 architecture a été précédemment appelée Extended Memory 64 Technology, et l’option du compilateur correspondante a été **/favor:EM64T**.

Pour plus d’informations sur la programmation pour le x64 architecture, consultez [x64 Conventions des logiciels](../../build/x64-software-conventions.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **C/C++** dossier.

1. Sélectionnez le **ligne de commande** page de propriétés.

1. Entrez l’option du compilateur dans le **des Options supplémentaires** boîte.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)