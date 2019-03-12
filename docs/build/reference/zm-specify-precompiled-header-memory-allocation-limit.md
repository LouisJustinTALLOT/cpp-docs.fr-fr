---
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
ms.openlocfilehash: 3c1362479b2068ee8fb527a4ecaac6e203e83cb0
ms.sourcegitcommit: dedd4c3cb28adec3793329018b9163ffddf890a4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/11/2019
ms.locfileid: "57751984"
---
# <a name="zm-specify-precompiled-header-memory-allocation-limit"></a>/Zm (Spécifier la limite d’allocation mémoire d’en-tête précompilé)

Détermine la quantité de mémoire que le compilateur alloue pour construire des en-têtes précompilés.

## <a name="syntax"></a>Syntaxe

```
/Zmfactor
```

## <a name="arguments"></a>Arguments

*factor*<br/>
Facteur d’échelle qui détermine la quantité de mémoire que le compilateur utilise pour construire des en-têtes précompilés.

Le *facteur* argument est un pourcentage de la taille par défaut d’une mémoire tampon de travail définie par le compilateur. La valeur par défaut *facteur* est 100 (pourcentage), mais vous pouvez spécifier des quantités plus grandes ou plus petites.

## <a name="remarks"></a>Notes

Dans les versions antérieures de Visual Studio 2015, le compilateur C++ utilisait plusieurs tas discrets, et chacun avait une limite finie. Actuellement, le compilateur dynamiquement augmente les tas selon les besoins, jusqu'à une limite de taille totale des tas et permet à l’en-tête précompilé devant inclure plusieurs plages d’adresses. Par conséquent, le **/Zm** option du compilateur est rarement nécessaire.

Si le compilateur manque d’espace de tas et émet le [C1060](../../error-messages/compiler-errors-1/fatal-error-c1060.md) message d’erreur lorsque vous utilisez le **/Zm** option du compilateur, vous avez pu réserver trop de mémoire. Envisagez de supprimer le **/Zm** option.

Si le compilateur émet le [C1076](../../error-messages/compiler-errors-1/fatal-error-c1076.md) accompagné d’un message d’erreur [C3859](../../error-messages/compiler-errors-2/compiler-error-c3859.md) message Spécifie le *facteur* argument à utiliser lorsque vous recompilez à l’aide de la **/Zm** option du compilateur. Ce message est significatif uniquement lorsqu’un en-tête précompilé utilise `#pragma hdrstop`. Dans d’autres cas, c’est une erreur de fausse causée par des problèmes de sollicitation de la mémoire virtuelle Windows et nous recommandons d’utiliser le **/Zm** option doit être ignorée. Au lieu de cela, envisagez de réduire le nombre de traitements parallèles lorsque vous utilisez le **/maxcpucount** option à MSBUILD. EXE conjointement avec le **/MP** option à CL. EXE. Pour plus d’informations, consultez [problèmes d’en-tête précompilé (PCH) et des recommandations](https://devblogs.microsoft.com/cppblog/precompiled-header-pch-issues-and-recommendations/).

Le tableau suivant montre comment la *facteur* argument a une incidence sur la limite d’allocation de mémoire si vous supposez que la taille du tampon en-tête précompilé par défaut est fixée à 75 Mo.

|Valeur de *facteur*|Limite d'allocation de mémoire|
|-----------------------|-----------------------------|
|10|7.5 MO|
|100|75 MO|
|200|150 MO|
|1000|750 MO|
|2 000|1 500 MO|

## <a name="other-ways-to-set-the-memory-allocation-limit"></a>Autres moyens de définir la limite d'allocation de mémoire

### <a name="to-set-the-zm-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir l'option de compilateur /Zm dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Dans le volet de navigation, sélectionnez **propriétés de Configuration** > **C/C++** > **ligne de commande**.

1. Entrez le **/Zm** option du compilateur dans le **des Options supplémentaires** boîte.

### <a name="to-set-the-zm-compiler-option-programmatically"></a>Pour définir l'option de compilateur /Zm par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)
