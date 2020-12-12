---
description: En savoir plus sur:/JMC (débogage Uniquement mon code)
title: /JMC (Débogage Uniquement mon code)
ms.date: 08/20/2018
f1_keywords:
- VC.Project.VCCLCompilerTool.SupportJustMyCode
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: 03a4cbc9bb9a992f2ed53e4f1239532923b32d0c
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199686"
---
# <a name="jmc-just-my-code-debugging"></a>/JMC (Débogage Uniquement mon code)

Spécifie la prise en charge du compilateur pour le débogage *uniquement mon code* natif dans le débogueur Visual Studio. Cette option prend en charge les paramètres utilisateur qui permettent à Visual Studio d’effectuer un pas à pas principal dans le système, l’infrastructure, la bibliothèque et d’autres appels non-utilisateur, ainsi que de réduire ces appels dans la fenêtre pile des appels. L’option du compilateur **/JMC** est disponible à partir de Visual Studio 2017 version 15,8.

## <a name="syntax"></a>Syntaxe

> **/JMC** \[ **-** ]

## <a name="remarks"></a>Notes

Les paramètres de [uniquement mon code](/visualstudio/debugger/just-my-code) de Visual Studio spécifient si le débogueur Visual Studio parcourt le système, le Framework, la bibliothèque et d’autres appels non-utilisateurs. L’option de compilateur **/JMC** permet la prise en charge de uniquement mon code débogage dans votre code C++ natif. Quand **/JMC** est activé, le compilateur insère les appels à une fonction d’assistance, `__CheckForDebuggerJustMyCode` , dans le prologue de la fonction. La fonction d’assistance fournit des raccordements qui prennent en charge le débogueur Visual Studio Uniquement mon code les opérations d’étape. Pour activer uniquement mon code dans le débogueur Visual Studio, dans la barre de menus, choisissez **Outils**  >  **options**, puis définissez l’option dans **débogage**  >  **général**  >  **activer uniquement mon code**.

L’option **/JMC** nécessite que votre code soit lié à la bibliothèque Runtime C (CRT), qui fournit la `__CheckForDebuggerJustMyCode` fonction d’assistance. Si votre projet n’est pas lié au CRT, vous pouvez voir l’erreur de l’éditeur de liens **LNK2019 : symbole externe non résolu __CheckForDebuggerJustMyCode**. Pour résoudre cette erreur, vous pouvez soit créer un lien vers la bibliothèque CRT, soit désactiver l’option **/JMC** .

Par défaut, l’option du compilateur **/JMC** est désactivée. Toutefois, à compter de Visual Studio 2017 version 15,8, cette option est activée dans la plupart des modèles de projet Visual Studio. Pour désactiver explicitement cette option, utilisez l’option **/JMC-** sur la ligne de commande. Dans Visual Studio, ouvrez la boîte de dialogue pages de propriétés du projet et modifiez la propriété **prise en charge uniquement mon code débogage** dans la page de propriétés général des **Propriétés de configuration**  >  **C/C++**  >   sur **non**.

Pour plus d’informations, consultez [c++ uniquement mon code](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) dans [spécifiez s’il faut déboguer uniquement le code utilisateur à l’aide de uniquement mon code dans Visual Studio](/visualstudio/debugger/just-my-code), et si le billet de Blog de l’équipe Visual C++ [annonce que C++ uniquement mon code pas à pas dans Visual Studio](https://devblogs.microsoft.com/cppblog/announcing-jmc-stepping-in-visual-studio/).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés général des **Propriétés de configuration**  >  **C/C++**  >   .

1. Modifiez la propriété **prise en charge du débogage uniquement mon code** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
