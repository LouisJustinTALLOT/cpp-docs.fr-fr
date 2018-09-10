---
title: -F (définir la taille de pile) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /f
dev_langs:
- C++
helpviewer_keywords:
- set stack size compiler option
- F compiler option [C++]
- -F compiler option [C++]
- /F compiler option [C++]
- stack, setting size
ms.assetid: 17320b6f-8305-445b-9ec2-75833f4b29e0
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 952933f72ae5d3f65aa646964ec6e04e758a27c6
ms.sourcegitcommit: 761c5f7c506915f5a62ef3847714f43e9b815352
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/07/2018
ms.locfileid: "44103773"
---
# <a name="f-set-stack-size"></a>/F (Définir la taille de pile)
Définit la taille de pile du programme en octets.

## <a name="syntax"></a>Syntaxe

> **/F** *nombre*

## <a name="arguments"></a>Arguments

*Nombre*<br/>
La taille de pile en octets.

## <a name="remarks"></a>Notes

Sans cette option, la taille de pile par défaut est 1 Mo. Le *nombre* argument peut être dans la notation décimale ou en langage C. L’argument peut varier de 1 à la taille de pile maximale acceptée par l’éditeur de liens. L’éditeur de liens arrondit la valeur spécifiée aux 4 octets plus proches. L’espace entre **/F** et *nombre* est facultatif.

Vous devrez peut-être augmenter la taille de pile si votre programme obtient les messages de débordement de pile.

Vous pouvez également définir la taille de pile :

-   À l’aide de la **/pile** option de l’éditeur de liens. Pour plus d’informations, consultez [/pile](../../build/reference/stack.md).

-   À l’aide de EDITBIN sur le fichier .exe. Pour plus d’informations, consultez [référence EDITBIN](../../build/reference/editbin-reference.md).

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **C/C++** > **ligne de commande** page de propriétés.

1. Tapez l'option de compilateur dans la zone **Options supplémentaires** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)   
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)