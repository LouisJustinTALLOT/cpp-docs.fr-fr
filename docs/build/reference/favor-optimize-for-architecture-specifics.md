---
description: En savoir plus sur:/favor (optimiser pour les caractéristiques de l’architecture)
title: /favor (optimisation pour les particularités d'architecture)
ms.date: 11/04/2016
f1_keywords:
- /favor
helpviewer_keywords:
- -favor compiler option [C++]
- /favor compiler option [C++]
ms.assetid: ad264df2-e30f-4d68-8bd0-10d6bee71a2a
ms.openlocfilehash: 184e81e1007214a09088601b6c579692a0dd20a7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192302"
---
# <a name="favor-optimize-for-architecture-specifics"></a>/favor (optimisation pour les particularités d'architecture)

**/favor :** `option` produit le code optimisé pour une architecture spécifique ou pour les caractéristiques des micro-architectures des architectures AMD et Intel.

## <a name="syntax"></a>Syntaxe

> **/favor :**{**Blend**  |  **Atom**  |  **amd64**  |  **Intel64**}

## <a name="remarks"></a>Notes

**/favor : Blend**<br/>
(x86 et x64) produit le code optimisé pour les caractéristiques des micro-architectures des architectures AMD et Intel. Alors que la fonction **/favor : Blend** peut ne pas offrir les meilleures performances possibles sur un processeur spécifique, il est conçu pour offrir des performances optimales sur une large gamme de processeurs x86 et x64. Par défaut, **/favor : Blend** est activé.

**/favor : ATOM**<br/>
(x86 et x64) produit le code qui est optimisé pour les caractéristiques du processeur Intel Atom et de la technologie de processeur Intel Centrino Atom. Le code généré à l’aide de **/favor : Atom** peut également produire des instructions Intel SSSE3, SSE3, SSE2 et SSE pour les processeurs Intel.

**/favor : AMD64**<br/>
(x64 uniquement) optimise le code généré pour les processeurs AMD Opteron et Athlon qui prennent en charge les extensions 64 bits. Le code optimisé peut s’exécuter sur toutes les plateformes compatibles x64. Le code généré à l’aide de **/favor : amd64** peut entraîner une dégradation des performances sur les processeurs Intel prenant en charge Intel64.

**/favor : INTEL64**<br/>
(x64 uniquement) optimise le code généré pour les processeurs Intel qui prennent en charge Intel64, ce qui donne généralement de meilleures performances pour cette plateforme. Le code résultant peut s’exécuter sur n’importe quelle plateforme x64. Le code généré avec **/favor : Intel64** peut entraîner une dégradation des performances sur les processeurs AMD Opteron et Athlon qui prennent en charge les extensions 64 bits.

> [!NOTE]
> L’architecture Intel64 était précédemment connue sous le nom de technologie de mémoire étendue 64, et l’option de compilateur correspondante était **/favor : EM64T**.

Pour plus d’informations sur la façon de programmer pour l’architecture x64, consultez conventions pour les [logiciels x64](../x64-software-conventions.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier **C/C++** .

1. Sélectionnez la page de propriétés **ligne de commande** .

1. Entrez l’option de compilateur dans la zone **options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
