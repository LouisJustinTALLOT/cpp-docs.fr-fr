---
description: En savoir plus sur:/Fe (nom de fichier EXE)
title: /Fe (Nom de fichier EXE)
ms.date: 11/04/2016
f1_keywords:
- /fe
helpviewer_keywords:
- -Fe compiler option [C++]
- executable files, renaming
- rename file compiler option [C++]
- /Fe compiler option [C++]
- Fe compiler option [C++]
ms.assetid: 49f594fd-5e94-45fe-a1bf-7c9f2abb6437
ms.openlocfilehash: 551c6f54ba75c71d9229b5a60ff0fdb192dbf100
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97192276"
---
# <a name="fe-name-exe-file"></a>/Fe (Nom de fichier EXE)

Spécifie un nom et un répertoire pour le fichier. exe ou la DLL créée par le compilateur.

## <a name="syntax"></a>Syntaxe

> **/Fe**[_chemin d’accès_] \
> **/Fe :** _nom de chemin_

### <a name="arguments"></a>Arguments

*chemin*<br/>
Le chemin d’accès relatif ou absolu et le nom de fichier de base, ou le chemin d’accès relatif ou absolu à un répertoire, ou le nom de fichier de base à utiliser pour l’exécutable généré.

## <a name="remarks"></a>Notes

L’option **/Fe** vous permet de spécifier le répertoire de sortie, le nom de l’exécutable de sortie, ou les deux, pour le fichier exécutable généré. Si *pathname* se termine par un séparateur de chemin d’accès (**&#92;**), il est supposé spécifier uniquement le répertoire de sortie. Dans le cas contraire, le dernier composant de *pathname* est utilisé comme nom de base du fichier de sortie, tandis que le reste du *chemin d’accès* spécifie le répertoire de sortie. Si *pathname* n’a pas de séparateurs de chemin d’accès, il est supposé spécifier le nom du fichier de sortie dans le répertoire actif. Le *chemin* d’accès doit être placé entre guillemets doubles (**"**) s’il contient des caractères qui ne peuvent pas être dans un chemin d’accès abrégé, tels que des espaces, des caractères étendus ou des composants de chemin d’accès comportant plus de huit caractères.

Lorsque l’option **/Fe** n’est pas spécifiée ou qu’un nom de base de fichier n’est pas spécifié dans *pathname*, le compilateur donne au fichier de sortie un nom par défaut à l’aide du nom de base du premier fichier source ou objet spécifié sur la ligne de commande et de l’extension. exe ou. dll.

Si vous spécifiez l’option [/c (compiler sans liaison)](c-compile-without-linking.md) , **/Fe** n’a aucun effet.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez la page de propriétés général de l’éditeur de liens **Propriétés de configuration**  >    >   .

1. Modifiez la propriété **fichier de sortie** . Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="examples"></a>Exemples

La ligne de commande suivante compile et lie tous les fichiers sources C dans le répertoire actif. Le fichier exécutable obtenu est nommé PROCESS.exe et est créé dans le répertoire « C:\Users\User Name\repos\My Project\bin ».

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

La ligne de commande suivante crée un fichier exécutable dans `C:\BIN` avec le même nom de base que le premier fichier source dans le répertoire actif :

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Spécification du chemin d’accès](specifying-the-pathname.md)<br/>
