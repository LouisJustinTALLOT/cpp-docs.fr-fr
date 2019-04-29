---
title: /F (Définir la taille de pile)
ms.date: 11/04/2016
f1_keywords:
- /f
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
ms.openlocfilehash: 9db595daa7de7820b594a8515ece7481b4382c98
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62293093"
---
# <a name="f-set-stack-size"></a>/F (Définir la taille de pile)

Définit la taille de pile du programme en octets.

## <a name="syntax"></a>Syntaxe

> **/F** *number*

## <a name="arguments"></a>Arguments

*number*<br/>
La taille de pile en octets.

## <a name="remarks"></a>Notes

Sans cette option, la taille de pile par défaut est 1 Mo. Le *nombre* argument peut être dans la notation décimale ou en langage C. L’argument peut varier de 1 à la taille de pile maximale acceptée par l’éditeur de liens. L’éditeur de liens arrondit la valeur spécifiée aux 4 octets plus proches. L’espace entre **/F** et *nombre* est facultatif.

Vous devrez peut-être augmenter la taille de pile si votre programme obtient les messages de débordement de pile.

Vous pouvez également définir la taille de pile :

- À l’aide de la **/pile** option de l’éditeur de liens. Pour plus d’informations, consultez [/pile](stack.md).

- À l’aide de EDITBIN sur le fichier .exe. Pour plus d’informations, consultez [référence EDITBIN](editbin-reference.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
