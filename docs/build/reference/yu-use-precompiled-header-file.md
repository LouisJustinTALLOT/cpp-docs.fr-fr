---
title: /Yu (Utiliser un fichier d’en-tête précompilé)
ms.date: 11/04/2016
f1_keywords:
- /yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: c0dcb045450d6e6eca31b8c76a92726e62400656
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57810115"
---
# <a name="yu-use-precompiled-header-file"></a>/Yu (Utiliser un fichier d’en-tête précompilé)

Indique au compilateur d’utiliser un fichier d’en-tête précompilé (.pch) existant dans la compilation actuelle.

## <a name="syntax"></a>Syntaxe

```
/Yu[filename]
```

## <a name="arguments"></a>Arguments

*filename*<br/>
Le nom d’un fichier d’en-tête, qui est inclus dans le fichier source en utilisant un **#include** directive de préprocesseur.

## <a name="remarks"></a>Notes

Le nom du fichier include doit être le même pour les deux le **/Yc** option qui crée l’en-tête précompilé et tout suivantes **/Yu** option indiquant l’utilisation de l’en-tête précompilé.

Pour **/Yc**, `filename` Spécifie le point sur la précompilation s’arrête ; le compilateur précompile tout le code `filename` et le nomme l’en-tête précompilé qui en résulte en utilisant le nom de base du fichier include et une extension de .pch.

Le fichier .pch doit avoir été créé avec **/Yc**.

Le compilateur traite tout le code qui précède le fichier .h comme étant précompilé. Il ignore Juste après le **#include** directive associée au fichier .h, utilise le code contenu dans le fichier .pch, puis compile tout le code après `filename`.

Sur la ligne de commande, aucun espace n’est autorisé entre **/Yu** et `filename`.

Lorsque vous spécifiez le **/Yu** option sans un nom de fichier, votre programme source doit contenir un [#pragma hdrstop](../../preprocessor/hdrstop.md) pragma qui spécifie le nom de fichier de l’en-tête précompilé, le fichier .pch. Dans ce cas, le compilateur utilisera l’en-tête précompilé (fichier .pch) nommé par  [ /fp (nom. Fichier PCH)](fp-name-dot-pch-file.md). Le compilateur ignore à l’emplacement de ce pragma, restaure l’état compilé à partir du fichier d’en-tête précompilé spécifié par le pragma, puis compile uniquement le code qui suit le pragma. Si **#pragma hdrstop** ne spécifie pas un nom de fichier, le compilateur recherche un fichier portant un nom dérivé du nom de base du fichier source avec une extension .pch. Vous pouvez également utiliser le **/FP** option pour spécifier un fichier .pch différent.

Si vous spécifiez le **/Yu** option sans un nom de fichier et ne parviennent pas à spécifier un **hdrstop** pragma, un message d’erreur est généré et la compilation échoue.

Si le **/Yc** `filename` et **/Yu** `filename` options se produisent sur la même ligne de commande et les deux référencent le même nom de fichier, **/Yc** `filename` prend priorité, la précompilation de tout le code jusqu'à et y compris le fichier nommé. Cette fonctionnalité simplifie l’écriture de makefiles.

Étant donné que les fichiers .pch contiennent des informations sur l’environnement de machine, ainsi que des informations d’adresse de mémoire sur le programme, vous devez uniquement utiliser un fichier pch sur l’ordinateur où il a été créé.

Pour plus d’informations sur les en-têtes précompilés, consultez :

- [/Y (En-têtes précompilés)](y-precompiled-headers.md)

- [Fichiers d’en-tête précompilés](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Spécifiez [/Yc (créer un fichier d’en-tête précompilé)](yc-create-precompiled-header-file.md) sur un fichier .cpp dans votre projet.

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Cliquez sur le dossier **C/C++** .

1. Cliquez sur le **en-têtes précompilés** page de propriétés.

1. Modifier le **Création/utilisation PCH via fichier** propriété ou le **Création/utilisation d’un en-tête précompilé** propriété.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="examples"></a>Exemples

Si le code suivant :

```
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

est compilé avec la ligne de commande `CL /YuMYAPP.H PROG.CPP`, le compilateur ne traite pas les trois instructions include, mais utilise le code précompilé du fichier MYAPP.pch ainsi l’enregistrement de l’heure impliqués dans les trois fichiers (et tous les fichiers qu’ils peuvent inclure) le prétraitement.

Vous pouvez utiliser le  [ /fp (nom. Fichier PCH)](fp-name-dot-pch-file.md) option avec la **/Yu** option pour spécifier le nom du fichier .pch si le nom est différent de l’argument nom de fichier de **/Yc** ou le nom de base du fichier source, comme dans le suivant :

```
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

Cette commande spécifie un fichier d’en-tête précompilé nommé MYPCH.pch. Le compilateur utilise son contenu pour restaurer l’état de tous les fichiers d’en-tête jusqu'à et y compris MYAPP.h précompilé. Le compilateur compile ensuite le code qui se produit après la MYAPP.h **incluent** instruction.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
