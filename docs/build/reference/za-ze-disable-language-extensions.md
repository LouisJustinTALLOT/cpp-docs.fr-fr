---
description: En savoir plus sur les éléments suivants:/za,/Ze (désactiver les extensions de langage)
title: /Za, /Ze (Désactiver les extensions de langage)
ms.date: 02/19/2019
f1_keywords:
- VC.Project.VCCLWCECompilerTool.DisableLanguageExtensions
- /za
- /ze
- VC.Project.VCCLCompilerTool.DisableLanguageExtensions
helpviewer_keywords:
- -Za compiler option [C++]
- Za compiler option [C++]
- language extensions, disabling in compiler
- -Ze compiler option [C++]
- language extensions
- enable language extensions
- /Za compiler option [C++]
- /Ze compiler option [C++]
- Disable Language Extensions compiler option
- Ze compiler option [C++]
ms.assetid: 65e49258-7161-4289-a176-7c5c0656b1a2
ms.openlocfilehash: 98b3d3a36a0aaf0731e6fe6ded06844f7f1e4213
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97263177"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Désactiver les extensions de langage)

L’option de compilateur **/za** désactive et émet des erreurs pour les extensions Microsoft en C qui ne sont pas compatibles avec ANSI C89/ISO C90. L’option de compilateur **/Ze** déconseillée active les extensions Microsoft. Les extensions Microsoft sont activées par défaut.

## <a name="syntax"></a>Syntaxe

> **/Za**\
> **/Ze**

## <a name="remarks"></a>Notes

> [!NOTE]
> L’utilisation de **/za** lorsque le code est compilé en C++ n’est pas recommandée. L’option **/Ze** est déconseillée, car son comportement est activé par défaut. Pour obtenir la liste des options du compilateur déconseillées, consultez [Options du compilateur déconseillées et supprimées](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options).

Le compilateur Microsoft C/C++ prend en charge la compilation du code C de deux manières :

- Le compilateur utilise le mode de compilation C par défaut lorsqu’un fichier source a une extension *. C* ou lorsque l’option [/TC](tc-tp-tc-tp-specify-source-file-type.md) ou [/TC](tc-tp-tc-tp-specify-source-file-type.md) est spécifiée. Le compilateur C est un compilateur C89/C90 qui, par défaut, active les extensions Microsoft du langage C. Pour plus d’informations sur les extensions spécifiques, consultez [extensions Microsoft pour C et C++](microsoft-extensions-to-c-and-cpp.md). Quand la compilation C et l’option **/za** sont toutes deux spécifiées, le compilateur c est strictement conforme à la norme C89/C90. Le compilateur traite les mots clés étendus Microsoft comme des identificateurs simples, désactive les autres extensions Microsoft et définit automatiquement la macro prédéfinie [ \_ \_ STDC \_ \_ ](../../preprocessor/predefined-macros.md) pour les programmes C.

- Le compilateur peut compiler du code C en mode de compilation C++. Ce comportement est le comportement par défaut pour les fichiers sources qui n’ont pas d’extension *. c* , et lorsque l’option [/TP](tc-tp-tc-tp-specify-source-file-type.md) ou [/TP](tc-tp-tc-tp-specify-source-file-type.md) est spécifiée. En mode de compilation C++, le compilateur prend en charge les parties des normes ISO C99 et C11 qui ont été incorporées dans la norme C++. Presque tout le code C est également un code C++ valide. Un petit nombre de mots clés C et de constructions de code ne sont pas des codes C++ valides, ou sont interprétés différemment en C++. Dans ces cas, le compilateur se comporte conformément à la norme C++. En mode de compilation C++, l’option **/za** peut provoquer un comportement inattendu et n’est pas recommandée.

D’autres options du compilateur peuvent affecter la façon dont le compilateur garantit la conformité aux normes. Pour savoir comment spécifier des paramètres de comportement standard C et C++ standard, consultez l’option du compilateur [/Zc](zc-conformance.md) . Pour obtenir d’autres paramètres de conformité C++ standard, consultez les options du compilateur [/permissive-](permissive-standards-conformance.md) et [/STD](std-specify-language-standard-version.md) .

Pour plus d’informations sur les problèmes de conformité avec Visual C++, consultez [comportement non standard](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans le volet de navigation, choisissez **Propriétés de configuration**  >  **langage C/C++**  >  .

1. Modifiez la propriété **désactivation des extensions de langage** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](compiler-options.md)<br/>
[/Zc (Conformité)](zc-conformance.md)<br/>
[/permissive - (Conformité aux standards)](permissive-standards-conformance.md)<br/>
[/STD (spécifier la version du langage standard)](std-specify-language-standard-version.md)<br/>
