---
description: En savoir plus sur:/yl (injecter une référence PCH pour la bibliothèque de débogage)
title: /Yl (Injecter une référence PCH pour une bibliothèque de débogage)
ms.date: 01/29/2018
f1_keywords:
- /yl
helpviewer_keywords:
- -Yl compiler option [C++]
- Yl compiler option [C++]
- /Yl compiler option [C++]
ms.assetid: 8e4a396a-6790-4a9f-8387-df015a3220e7
ms.openlocfilehash: f1d05b4e0c38377233e9aaf6299227f7fbaebd55
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97151851"
---
# <a name="yl-inject-pch-reference-for-debug-library"></a>/Yl (Injecter une référence PCH pour une bibliothèque de débogage)

L’option **/yl** génère un symbole unique dans un fichier d’en-tête précompilé, et une référence à ce symbole est injectée dans tous les fichiers objets qui utilisent l’en-tête précompilé.

## <a name="syntax"></a>Syntaxe

>**/YL**\
>**/Yl**_nom_\
>**/YL-**

### <a name="arguments"></a>Arguments

*name*<br/>
Nom facultatif utilisé dans le cadre du symbole unique.

*\-*<br/>
Un tiret (-) désactive explicitement l’option de compilateur **/yl** .

## <a name="remarks"></a>Notes

L’option de compilateur **/yl** crée une définition de symbole unique dans un fichier d’en-tête précompilé créé à l’aide de l’option [/Yc](yc-create-precompiled-header-file.md) . Les références à ce symbole sont automatiquement injectées dans tous les fichiers qui incluent l’en-tête précompilé à l’aide de l’option du compilateur [/Yu](yu-use-precompiled-header-file.md) . L’option **/yl** est activée par défaut lorsque **/Yc** est utilisé pour créer un fichier d’en-tête précompilé.

L’option **/yl**_Name_ est utilisée pour créer un symbole identifiable dans le fichier d’en-tête précompilé. Le compilateur utilise l’argument *Name* dans le nom de symbole décoré qu’il crée, à l’instar de `__@@_PchSym_@00@...@name` , où les points de suspension (...) représentent une chaîne de caractères unique générée par le compilateur. Si l’argument *Name* est omis, le compilateur génère automatiquement un nom de symbole. Normalement, vous n’avez pas besoin de connaître le nom du symbole. Toutefois, lorsque votre projet utilise plusieurs fichiers d’en-tête précompilés, l’option **/yl**_Name_ peut être utile pour déterminer les fichiers objets qui utilisent l’en-tête précompilé. Vous pouvez utiliser *Name* comme chaîne de recherche pour rechercher la référence de symbole dans un fichier de vidage.

**/Yl-** désactive le comportement par défaut et ne place pas de symbole d’identification dans le fichier d’en-tête précompilé. Les fichiers compilés qui incluent cet en-tête précompilé n’obtiennent pas de référence de symbole commune.

Lorsque **/Yc** n’est pas spécifié, toute option **/yl** n’a aucun effet, mais si elle est spécifiée, elle doit correspondre à n’importe quelle option **/yl** transmise lorsque **/Yc** est spécifié.

Si vous utilisez les options **/yl-**, **/Yc** et [/Z7](z7-zi-zi-debug-information-format.md) pour générer un fichier d’en-tête précompilé, les informations de débogage sont stockées dans le fichier objet pour le fichier source utilisé pour créer l’en-tête précompilé, plutôt que dans un fichier. pdb distinct. Si ce fichier objet fait partie d’une bibliothèque, des erreurs [LNK1211](../../error-messages/tool-errors/linker-tools-error-lnk1211.md) ou des avertissements [LNK4206](../../error-messages/tool-errors/linker-tools-warning-lnk4206.md) peuvent se produire dans les builds qui utilisent cette bibliothèque et le fichier d’en-tête précompilé, si le fichier source utilisé pour créer le fichier d’en-tête précompilé ne définit pas les symboles lui-même. L’éditeur de liens peut exclure le fichier objet du lien, ainsi que les informations de débogage associées, lorsque rien dans le fichier objet n’est référencé dans le client de bibliothèque. Pour résoudre ce problème, spécifiez **/yl** (ou supprimez l’option **/yl-** ) quand vous utilisez **/Yc** pour créer le fichier d’en-tête précompilé. Cela permet de s’assurer que le fichier objet de la bibliothèque qui contient les informations de débogage est lié dans votre Build.

Pour plus d’informations sur les en-têtes précompilés, consultez :

- [/Y (en-têtes précompilés)](y-precompiled-headers.md)

- [Fichiers d’en-tête précompilés](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Ajoutez l’option de compilateur **/yl**_Name_ dans la zone **options supplémentaires** . Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
