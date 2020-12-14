---
description: En savoir plus sur:/F (définir la taille de la pile)
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
ms.openlocfilehash: 5bf8b0855c65fc39caf8935b06a877c62a4e0df0
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97200778"
---
# <a name="f-set-stack-size"></a>/F (Définir la taille de pile)

Définit la taille de la pile du programme en octets.

## <a name="syntax"></a>Syntaxe

> **/F** *nombre*

## <a name="arguments"></a>Arguments

*number*<br/>
Taille de la pile en octets.

## <a name="remarks"></a>Notes

Sans cette option, la taille de la pile par défaut est de 1 Mo. L’argument *Number* peut être en notation décimale ou de langage C. L’argument peut être compris entre 1 et la taille de pile maximale acceptée par l’éditeur de liens. L’éditeur de liens arrondit la valeur spécifiée aux 4 octets les plus proches. L’espace entre **/f** et *Number* est facultatif.

Vous devrez peut-être augmenter la taille de la pile si votre programme reçoit des messages de dépassement de capacité de la pile.

Vous pouvez également définir la taille de la pile de la façon suivante :

- À l’aide de l’option **/Stack** de l’éditeur de liens. Pour plus d’informations, consultez [/Stack](stack.md).

- À l’aide de EDITBIN sur le fichier. exe. Pour plus d’informations, consultez [référence EDITBIN](editbin-reference.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >   .

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
