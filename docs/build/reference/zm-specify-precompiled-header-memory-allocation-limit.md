---
description: En savoir plus sur:/ZM (spécifier la limite d’allocation de mémoire d’en-tête précompilé)
title: /Zm (Spécifier la limite d’allocation mémoire d’en-tête précompilé)
ms.date: 03/08/2019
f1_keywords:
- /zm
helpviewer_keywords:
- PCH files, memory allocation limit
- Zm compiler option [C++]
- /Zm compiler option [C++]
- precompiled header files, memory allocation limit
- Specify Precompiled Header Memory Allocation Limit compiler option
- cl.exe compiler, memory allocation limit
- .pch files, memory allocation limit
- memory allocation, Memory Allocation Limit compiler option
- -Zm compiler option [C++]
ms.assetid: 94c77d5e-6672-46a7-92e0-3f69e277727d
ms.openlocfilehash: 624d8926961d9ca3d32ef204b70683c14dc3197f
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224385"
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm (Spécifier la limite d’allocation mémoire d’en-tête précompilé)

Détermine la quantité de mémoire que le compilateur alloue pour construire des en-têtes précompilés.

## <a name="syntax"></a>Syntaxe

```
/Zmfactor
```

## <a name="arguments"></a>Arguments

*factorisés*<br/>
Facteur d’échelle qui détermine la quantité de mémoire que le compilateur utilise pour construire des en-têtes précompilés.

L’argument *Factor* est un pourcentage de la taille par défaut d’une mémoire tampon de travail définie par le compilateur. La valeur par défaut du *facteur* est 100 (en pourcentage), mais vous pouvez spécifier des montants plus grands ou plus petits.

## <a name="remarks"></a>Notes

Dans les versions antérieures à Visual Studio 2015, le compilateur C++ utilisait plusieurs tas discrets, chacun possédant une limite finie. Actuellement, le compilateur augmente dynamiquement les tas selon les besoins, jusqu’à une limite de taille de tas totale, et permet à l’en-tête précompilé de contenir plusieurs plages d’adresses. Par conséquent, l’option de compilateur **/ZM** est rarement nécessaire.

Si le compilateur manque d’espace de tas et émet le message d’erreur [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) quand vous utilisez l’option de compilateur **/ZM** , vous avez peut-être réservé trop de mémoire. Envisagez de supprimer l’option **/ZM** .

Si le compilateur émet le message d’erreur [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) , un message [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) associé spécifie l’argument *Factor* à utiliser lorsque vous recompilez à l’aide de l’option du compilateur **/ZM** . Ce message est significatif uniquement lorsqu’un en-tête précompilé utilise `#pragma hdrstop` . Dans d’autres cas, il s’agit d’une erreur parasite causée par des problèmes de sollicitation de la mémoire virtuelle Windows, et la recommandation d’utiliser l’option **/ZM** doit être ignorée. Au lieu de cela, envisagez de réduire le nombre de processus parallèles lorsque vous utilisez l’option **/maxcpucount** pour MSBUILD.EXE conjointement avec l’option **/MP** pour CL.EXE. Pour plus d’informations, consultez [problèmes et recommandations concernant les en-têtes précompilés (PCH)](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

Le tableau suivant montre comment l’argument *Factor* affecte la limite d’allocation de mémoire si vous supposez que la taille de la mémoire tampon d’en-tête précompilé par défaut est de 75 Mo.

|Valeur du *facteur*|Limite d'allocation de mémoire|
|-----------------------|-----------------------------|
|10|7,5 Mo|
|100|75 MO|
|200|150 MO|
|1 000|750 Mo|
|2000|1 500 Mo|

## <a name="other-ways-to-set-the-memory-allocation-limit"></a>Autres moyens de définir la limite d'allocation de mémoire

### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir l'option de compilateur /Zm dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Dans le volet de navigation, sélectionnez **Propriétés de configuration**  >  ligne de commande **C/C++**  >  .

1. Entrez l’option du compilateur **/ZM** dans la zone **options supplémentaires** .

### <a name="to-set-the-zm-compiler-option-programmatically"></a>Pour définir l'option de compilateur /Zm par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
