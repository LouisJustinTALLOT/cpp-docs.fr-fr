---
description: 'En savoir plus sur : `/Yu` (utiliser un fichier d’en-tête précompilé)'
title: /Yu (Utiliser un fichier d’en-tête précompilé)
ms.date: 07/31/2020
f1_keywords:
- /Yu
helpviewer_keywords:
- Yu compiler option [C++]
- /Yu compiler option [C++]
- -Yu compiler option [C++]
- PCH files, use existing
- .pch files, use existing
- precompiled header files, use existing
ms.assetid: 24f1bd0e-b624-4296-a17e-d4b53e374e1f
ms.openlocfilehash: 7076a3a4dd9183a3a0072fa6211acbb0b95a4865
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97229961"
---
# <a name="yu-use-precompiled-header-file"></a>`/Yu` (Utiliser le fichier d’en-tête précompilé)

Indique au compilateur d’utiliser un fichier d’en-tête précompilé ( *`.pch`* ) existant dans la compilation actuelle.

## <a name="syntax"></a>Syntaxe

> **`/Yu`**\[*nom du fichier*]

## <a name="arguments"></a>Arguments

*extension*<br/>
Nom d’un fichier d’en-tête, qui est inclus dans le fichier source à l’aide d’une `#include` directive de préprocesseur.

## <a name="remarks"></a>Notes

Le nom du fichier include doit être le même pour l' **`/Yc`** option qui crée l’en-tête précompilé et pour toute **`/Yu`** option ultérieure qui indique l’utilisation de l’en-tête précompilé.

Pour **`/Yc`** , *filename* spécifie le point auquel la précompilation s’arrête ; le compilateur précompile tout le  code par le biais du nom de fichier et nomme l’en-tête précompilé résultant en utilisant le nom de base du fichier include et une extension de *`.pch`* .

Le *`.pch`* fichier doit avoir été créé à l’aide de **`/Yc`** .

Le compilateur traite tout le code qui se trouve avant le fichier. h comme étant précompilé. Elle ignore juste au-delà de la `#include` directive associée au *`.h`* fichier, utilise le code contenu dans le *`.pch`* fichier, puis compile tout le code après *filename*.

Sur la ligne de commande, aucun espace n’est autorisé entre **`/Yu`** et *nom de fichier*.

Lorsque vous spécifiez l' **`/Yu`** option sans nom de fichier, votre programme source doit contenir un [`#pragma hdrstop`](../../preprocessor/hdrstop.md) pragma qui spécifie le nom de fichier de l’en-tête précompilé, *`.pch`* file. Dans ce cas, le compilateur utilise l’en-tête précompilé ( *`.pch`* fichier) nommé par [`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) . Le compilateur passe à l’emplacement de ce pragma et restaure l’État compilé à partir du fichier d’en-tête précompilé spécifié. Elle compile ensuite uniquement le code qui suit le pragma. Si `#pragma hdrstop` ne spécifie pas de nom de fichier, le compilateur recherche un fichier dont le nom est dérivé du nom de base du fichier source avec une *`.pch`* extension. Vous pouvez également utiliser l' **`/Fp`** option pour spécifier un autre *`.pch`* fichier.

Si vous spécifiez l' **`/Yu`** option sans nom de fichier et que vous ne parvenez pas à spécifier un `hdrstop` pragma, un message d’erreur est généré et la compilation échoue.

Si les **`/Yc`** options de _nom de_ fichier et de fichier **`/Yu`**  se produisent sur la même ligne de commande et qu’elles référencent le même nom de fichier, le **`/Yc`** _nom_ de fichier est prioritaire, précompilation de tout le code jusqu’au fichier nommé inclus. Cette fonctionnalité simplifie l’écriture de makefiles.

Étant donné que les *`.pch`* fichiers contiennent des informations sur l’environnement de l’ordinateur et les informations d’adresse mémoire sur le programme, vous devez uniquement utiliser un *`.pch`* fichier sur l’ordinateur sur lequel il a été créé.

Pour plus d’informations sur les en-têtes précompilés, consultez :

- [`/Y` (En-têtes précompilés)](y-precompiled-headers.md)

- [Fichiers d’en-tête précompilés](../creating-precompiled-header-files.md)

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Spécifiez [ `/Yc` (créer un fichier d’en-tête précompilé)](yc-create-precompiled-header-file.md) sur un fichier. cpp de votre projet.

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés **Propriétés de configuration**  >    >  **en-têtes précompilés** C/C++.

1. Modifiez la propriété d' **en-tête précompilé** , la propriété **créer/utiliser PCH par le fichier** ou la propriété d' **en-tête précompilé créer/utiliser** .

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Localisez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.PrecompiledHeaderThrough%2A> et <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.UsePrecompiledHeader%2A>.

## <a name="example"></a>Exemple

Si le code suivant :

```cpp
#include <afxwin.h>   // Include header for class library
#include "resource.h" // Include resource definitions
#include "myapp.h"    // Include information specific to this app
...
```

est compilé à l’aide de la ligne de commande `CL /YuMYAPP.H PROG.CPP` , le compilateur ne traite pas les trois instructions include. Au lieu de cela, il utilise le code précompilé de *`MYAPP.pch`* , ce qui permet de gagner du temps lors du prétraitement des trois fichiers (et de tous les fichiers qu’ils peuvent inclure).

Vous pouvez utiliser l' [`/Fp (Name .pch file)`](fp-name-dot-pch-file.md) option avec l' **`/Yu`** option pour spécifier le nom du *`.pch`* fichier si le nom est différent de l’argument de *nom* de fichier à **`/Yc`** ou du nom de base du fichier source, comme dans l’exemple suivant :

```cmd
CL /YuMYAPP.H /FpMYPCH.pch PROG.CPP
```

Cette commande spécifie un fichier d’en-tête précompilé nommé *`MYPCH.pch`* . Le compilateur utilise son contenu pour restaurer l’état précompilé de tous les fichiers d’en-tête jusqu’à et y compris *`MYAPP.h`* . Le compilateur compile ensuite le code qui se produit après la `#include "MYAPP.h"` directive *.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
