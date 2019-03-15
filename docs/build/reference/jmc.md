---
title: / JMC (débogage uniquement mon Code)
ms.date: 08/20/2018
f1_keywords:
- /JMC
helpviewer_keywords:
- /JMC compiler option [C++]
- Just my code [C++]
- -JMC compiler option [C++]
- User code, debugging
- JMC compiler option [C++]
ms.openlocfilehash: c107ad7107d2a65ed19719933aa127c0557916ce
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57808051"
---
# <a name="jmc-just-my-code-debugging"></a>/ JMC (débogage uniquement mon Code)

Spécifie la prise en charge du compilateur pour natif *uniquement mon Code* débogage dans le débogueur Visual Studio. Cette option prend en charge les paramètres de l’utilisateur qui permettent à Visual Studio pour effectuer un survol de système, de framework, de bibliothèque et d’autres appels non utilisateur et pour réduire ces appels dans la fenêtre Pile des appels. Le **/JMC** option du compilateur est disponible à partir de Visual Studio 2017 version 15.8.

## <a name="syntax"></a>Syntaxe

> **/JMC**\[**-**]

## <a name="remarks"></a>Notes

Visual Studio [uniquement mon Code](/visualstudio/debugger/just-my-code) paramètres spécifient si le débogueur Visual Studio étapes sur le système, de framework, de bibliothèque et d’autres appels non utilisateur. Le **/JMC** option du compilateur permet la prise en charge de débogage uniquement mon Code dans votre code C++ natif. Lorsque **/JMC** est activé, le compilateur insère les appels à une fonction d’assistance, `__CheckForDebuggerJustMyCode`, dans le prologue de fonction. La fonction d’assistance fournit des hooks qui prennent en charge les opérations des étapes d’uniquement mon Code débogueur Visual Studio. Pour activer uniquement mon Code dans le débogueur Visual Studio, dans la barre de menus, choisissez **outils** > **Options**, puis définissez l’option de **débogage**  >  **Général** > **activer uniquement mon Code**.

Le **/JMC** option nécessite que votre code lié à la bibliothèque Runtime C (CRT), qui fournit le `__CheckForDebuggerJustMyCode` fonction d’assistance. Si votre projet ne pointe pas vers la bibliothèque CRT, vous pouvez voir des erreurs de l’éditeur de liens **LNK2019 : non résolu de symbole externe __CheckForDebuggerJustMyCode**. Pour résoudre cette erreur, lier à la bibliothèque CRT, soit désactiver le **/JMC** option.

Par défaut, le **/JMC** option du compilateur est désactivée. Toutefois, à compter de Visual Studio 2017 version 15.8 cette option est activée dans la plupart des modèles de projet Visual Studio. Pour désactiver explicitement cette option, utilisez le **/JMC-** option sur la ligne de commande. Dans Visual Studio, ouvrez la boîte de dialogue des Pages de propriétés de projet et de modifier le **prise en charge uniquement mon Code débogage** propriété dans le **propriétés de Configuration** > **C/C++**  >  **Général** page de propriétés **non**.

Pour plus d’informations, consultez [C++ uniquement mon Code](/visualstudio/debugger/just-my-code#BKMK_C___Just_My_Code) dans [Indiquez si vous souhaitez déboguer uniquement le code utilisateur à l’aide d’uniquement mon Code dans Visual Studio](/visualstudio/debugger/just-my-code)et le billet de Blog de l’équipe Visual C++ [annonce C++ uniquement mon Code Pas à pas dans Visual Studio](https://blogs.msdn.microsoft.com/vcblog/2018/06/29/announcing-jmc-stepping-in-visual-studio/).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **général** page de propriétés.

1. Modifier le **prise en charge uniquement mon Code débogage** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
