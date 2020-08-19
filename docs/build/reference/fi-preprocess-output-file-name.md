---
title: /Fi (prétraiter le nom du fichier de sortie)
ms.date: 08/12/2020
f1_keywords:
- /Fi
helpviewer_keywords:
- Fi compiler option (C++)
- -Fi compiler option (C++)
- /Fi compiler option (C++)
- preprocessing output files, file name
ms.assetid: 6d0ba983-a8b7-41ec-84f5-b4688ef8efee
ms.openlocfilehash: 82bf09a8f01f656f90ad9971530b05f108fc95a4
ms.sourcegitcommit: 1839405b97036891b6e4d37c99def044d6f37eff
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/18/2020
ms.locfileid: "88561087"
---
# <a name="fi-preprocess-output-file-name"></a>`/Fi` (Prétraiter le nom du fichier de sortie)

Spécifie le nom du fichier de sortie dans lequel l’option de compilateur [ `/P` (Prétraiter dans un fichier)](p-preprocess-to-a-file.md) écrit la sortie prétraitée.

## <a name="syntax"></a>Syntaxe

> **`/Fi`**_`pathname`_

### <a name="parameters"></a>Paramètres

*`pathname`*\
Chemin d’accès relatif ou absolu et nom de fichier du fichier de sortie généré par l' **`/P`** option de compilateur. Ou, le chemin d’accès au répertoire pour les *`.i`* fichiers de sortie lorsque plusieurs fichiers d’entrée sont spécifiés. Ne placez pas d’espace entre l' **`/Fi`** option et *`pathname`* .

## <a name="remarks"></a>Notes

Utilisez l' **`/Fi`** option du compilateur en association avec l' **`/P`** option du compilateur. Si **`/P`** n’est pas spécifié, **`/Fi`** provoque l’avertissement de ligne de commande D9007.

Si vous spécifiez uniquement un chemin d’accès de répertoire (un chemin d’accès qui se termine par une barre oblique inverse **`\`** ) pour le *`pathname`* paramètre, le nom de base du fichier source est utilisé comme nom de base du fichier de sortie prétraité. Le *`pathname`* paramètre ne requiert pas d’extension de nom de fichier particulière. Toutefois, une extension de « . i » est utilisée si vous ne spécifiez pas d’extension de nom de fichier.

### <a name="example"></a>Exemple

La ligne de commande suivante prétraite *`PROGRAM.cpp`* , conserve les commentaires, ajoute des [`#line`](../../preprocessor/hash-line-directive-c-cpp.md) directives et écrit le résultat dans le *`MYPROCESS.i`* fichier :

```cmd
CL /P /FiMYPROCESS.I PROGRAM.CPP
```

Cette ligne de commande prétraite *`main.cpp`* et *`helper.cpp`* into *`main.i`* et *`helper.i`* dans un sous-répertoire nommé *`preprocessed`* :

```cmd
CL /P /Fi".\\preprocessed\\" main.cpp helper.cpp
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez le fichier source ou la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés de **Configuration Propriétés**du  >  préprocesseur**C/C++**  >  **Preprocessor** .

1. Définissez le **prétraitement sur** **Oui**comme valeur de la propriété de fichier.

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Entrez l' **`/Fi`** option du compilateur et *`pathname`* dans la zone **options supplémentaires** . Spécifiez uniquement un chemin d’accès de répertoire, et non un nom de fichier, lors de la définition de cette propriété pour un projet.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCCLCompilerTool.AdditionalOptions%2A>.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[`/P` (Prétraiter dans un fichier)](p-preprocess-to-a-file.md)<br/>
[Spécification du nom de chemin](specifying-the-pathname.md)
