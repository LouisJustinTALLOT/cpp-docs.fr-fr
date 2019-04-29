---
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
ms.openlocfilehash: 1db1dbdba4829ccf939cdc4f07ccfefe2474a35d
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62315883"
---
# <a name="za-ze-disable-language-extensions"></a>/Za, /Ze (Désactiver les extensions de langage)

Le **/Za** option du compilateur désactive et émet des erreurs des extensions Microsoft pour C et qui ne sont pas compatibles avec ANSI/ISO C89 C90. Déconseillées **/Ze** option du compilateur Active les extensions Microsoft. Les extensions Microsoft sont activées par défaut.

## <a name="syntax"></a>Syntaxe

> **/Za**<br/>
> **/Ze**

## <a name="remarks"></a>Notes

> [!NOTE]
> L’utilisation de **/Za** lorsque le code est compilé comme C++ n’est pas recommandé. Le **/Ze** option est déconseillée, car son comportement est activé par défaut. Pour obtenir la liste des options du compilateur déconseillées, consultez [déconseillées et des options du compilateur supprimé](compiler-options-listed-by-category.md#deprecated-and-removed-compiler-options).

Le compilateur Microsoft C/C++ prend en charge la compilation de code C de deux manières :

- Le compilateur utilise le mode de compilation C par défaut lorsqu’un fichier source a un *.c* extension, ou lorsque le [TP](tc-tp-tc-tp-specify-source-file-type.md) ou [TP](tc-tp-tc-tp-specify-source-file-type.md) option est spécifiée. Le compilateur C est un compilateur C89/C90 permettant, par défaut, les extensions Microsoft du langage C. Pour plus d’informations sur les extensions spécifiques, consultez [Extensions Microsoft pour C et C++](microsoft-extensions-to-c-and-cpp.md). Lorsque les deux compilation C et le **/Za** option sont spécifiés, le compilateur C respecte strictement la norme C89/C90. Le compilateur traite l’étendue des mots clés comme identificateurs simples Microsoft, désactive les autres extensions Microsoft et définit automatiquement la [ \_ \_STDC\_ \_ ](../../preprocessor/predefined-macros.md) prédéfinis macro pour les programmes C.

- Le compilateur peut compiler du code C en mode de compilation de C++. Ce comportement est la valeur par défaut pour les fichiers sources qui n’ont pas un *.c* extension et à quel moment le [/Tp](tc-tp-tc-tp-specify-source-file-type.md) ou [/TP](tc-tp-tc-tp-specify-source-file-type.md) option est spécifiée. En mode de compilation de C++, le compilateur prend en charge les parties des normes ISO C99 et C11 qui ont été incorporés à la norme C++. Presque tout le code C est également valide du code C++. Un petit nombre de mots clés C et les constructions de code ne sont pas du code C++ valide, ou est interprété différemment en C++. Le compilateur se comporte en fonction de la norme dans ces cas C++. En mode de compilation de C++, le **/Za** option peut entraîner un comportement inattendu et n’est pas recommandée.

Autres options du compilateur peuvent affecter la façon dont le compilateur garantit la conformité aux normes. Pour les méthodes permettant de spécifier des paramètres spécifiques de comportement de C et C++ standards, consultez le [/Zc](zc-conformance.md) option du compilateur. Pour les paramètres de conformité standard C++ supplémentaires, consultez le [/ permissive-](permissive-standards-conformance.md) et [/STD](std-specify-language-standard-version.md) options du compilateur.

Pour plus d’informations sur les problèmes de conformité avec Visual C++, consultez [comportement non standard](../../cpp/nonstandard-behavior.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Dans le volet de navigation, choisissez **propriétés de Configuration** > **C/C++** > **langage**.

1. Modifier le **désactiver les Extensions de langage** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.DisableLanguageExtensions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](compiler-options.md)<br/>
[/Zc (Conformité)](zc-conformance.md)<br/>
[/permissive - (Conformité aux normes)](permissive-standards-conformance.md)<br/>
[/std (Spécifier la version de langue standard)](std-specify-language-standard-version.md)<br/>
