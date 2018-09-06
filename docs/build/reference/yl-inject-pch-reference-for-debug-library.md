---
title: -Yl (injecter une référence PCH pour une bibliothèque de débogage) | Microsoft Docs
ms.custom: ''
ms.date: 01/29/2018
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /yl
dev_langs:
- C++
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 1fda6ac3336b1f2a5e910355b5460633916b0803
ms.sourcegitcommit: d10a2382832373b900b1780e1190ab104175397f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/06/2018
ms.locfileid: "43894653"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Injecter une référence PCH pour une bibliothèque de débogage)

Le **/Yl** option génère un symbole unique dans un fichier d’en-tête précompilé, et une référence à ce symbole est injectée dans tous les fichiers d’objets qui utilisent l’en-tête précompilé.

## <a name="syntax"></a>Syntaxe

>**/Yl**  
>**/YL**_nom_  
>**/Yl-**  

### <a name="arguments"></a>Arguments

*name*  
Nom facultatif utilisé dans le cadre du symbole unique.

*\-*  
Un tiret (-) désactive explicitement la **/Yl** option du compilateur.

## <a name="remarks"></a>Notes

Le **/Yl** option du compilateur crée une définition de symbole unique dans un fichier d’en-tête précompilé créé à l’aide de la [/Yc](../../build/reference/yc-create-precompiled-header-file.md) option. Références à ce symbole sont automatiquement injectés dans tous les fichiers qui incluent l’en-tête précompilé à l’aide de la [/Yu](../../build/reference/yu-use-precompiled-header-file.md) option du compilateur. Le **/Yl** option est activée par défaut lorsque **/Yc** est utilisé pour créer un fichier d’en-tête précompilé.

Le **/Yl**_nom_ option est utilisée pour créer un symbole d’identification dans le fichier d’en-tête précompilé. Le compilateur utilise le *nom* argument en tant que partie du nom décoré symbole qu’elle crée, similaire à `__@@_PchSym_@00@...@name`, où la chaîne de caractères représente de points de suspension (...) une valeur unique générée par le compilateur. Si le *nom* argument est omis, le compilateur génère un nom de symbole automatiquement. Normalement, vous n’avez pas besoin de connaître le nom du symbole. Toutefois, lorsque votre projet utilise plus d’un fichier d’en-tête précompilé, le **/Yl**_nom_ option peut être utile pour déterminer quel objet de fichiers utilisent ce qui est l’en-tête précompilé. Vous pouvez utiliser *nom* comme une chaîne de recherche pour trouver la référence de symbole dans un fichier de vidage.

**/YL-** désactive le comportement par défaut et ne pas placer un symbole d’identification dans le fichier d’en-tête précompilé. Les fichiers compilés qui incluent cet en-tête précompilé n’obtiennent pas une référence de symboles courants.

Lorsque **/Yc** n’est pas spécifié, n’importe quel **/Yl** option n’a aucun effet, mais si elle doit correspondre à toute la spécifiée **/Yl** quand passée à l’option **/Yc** est spécifié.

Si vous utilisez **/Yl-**, **/Yc** et [/Z7](../../build/reference/z7-zi-zi-debug-information-format.md) options pour générer un fichier d’en-tête précompilé, les informations de débogage est stocké dans le fichier d’objet pour le fichier source utilisé pour créer le en-tête précompilé, plutôt que d’un fichier .pdb distinct. Si ce fichier objet est alors effectué dans une bibliothèque, [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) erreurs ou [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) avertissements peuvent se produire dans les builds qui utilisent cette bibliothèque et le fichier d’en-tête précompilé, si le fichier source utilisé pour créer le fichier d’en-tête précompilé ne définit aucun symbole lui-même. L’éditeur de liens peut exclure le fichier de l’objet à partir du lien, ainsi que les informations de débogage associées, lorsque rien dans le fichier objet est référencé dans le client de bibliothèque. Pour résoudre ce problème, spécifiez **/Yl** (ou de supprimer le **/Yl-** option) lorsque vous utilisez **/Yc** pour créer le fichier d’en-tête précompilé. Cela garantit que le fichier de l’objet à partir de la bibliothèque qui contient les informations de débogage est lié dans votre build.

Pour plus d’informations sur les en-têtes précompilés, consultez :

- [/Y (En-têtes précompilés)](../../build/reference/y-precompiled-headers.md)

- [Création de fichiers d’en-tête précompilé](../../build/reference/creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Ajouter le **/Yl**_nom_ option du compilateur dans le **des Options supplémentaires** boîte. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)  
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)  
