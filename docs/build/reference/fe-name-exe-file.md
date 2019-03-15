---
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
ms.openlocfilehash: 5901ef1997cfea84c97b6d91b30335ff7dbc1d9f
ms.sourcegitcommit: 8105b7003b89b73b4359644ff4281e1595352dda
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/14/2019
ms.locfileid: "57818048"
---
# <a name="fe-name-exe-file"></a>/Fe (Nom de fichier EXE)

Spécifie un nom et un répertoire pour le fichier .exe ou DLL créé par le compilateur.

## <a name="syntax"></a>Syntaxe

> **/Fe**[_pathname_] **/Fe :** _chemin d’accès_

### <a name="arguments"></a>Arguments

*pathname*<br/>
Le chemin d’accès relatif ou absolu et nom de fichier de base ou un chemin relatif ou absolu à un répertoire ou le nom de fichier de base à utiliser pour le fichier exécutable généré.

## <a name="remarks"></a>Notes

Le **/Fe** option vous permet de spécifier le répertoire de sortie, nom de fichier exécutable de sortie ou les deux, pour le fichier exécutable généré. Si *pathname* se termine par un séparateur de chemin d’accès (**&#92;**), il est supposé pour spécifier uniquement le répertoire de sortie. Sinon, le dernier composant de *pathname* est utilisé comme nom de base de fichier de sortie et le reste de *pathname* Spécifie le répertoire de sortie. Si *pathname* ne dispose pas des séparateurs de chemin d’accès, il est supposé pour spécifier le nom de fichier de sortie dans le répertoire actif. Le *pathname* doit être entourée de guillemets doubles (**»**) si elle contient des caractères qui ne peut pas être dans un chemin d’accès court, tels que des espaces, des caractères ou des composants de chemin d’accès plus de huit caractères étendus long.

Lorsque le **/Fe** option n’est pas spécifiée, ou quand un fichier base nom n’est pas spécifié dans *pathname*, le compilateur attribue le fichier de sortie d’un nom par défaut en utilisant le nom de base du premier fichier source ou un objet spécifié sur la ligne de commande et l’extension .exe ou .dll.

Si vous spécifiez le [/c (compiler sans liaison)](c-compile-without-linking.md) option, **/Fe** n’a aucun effet.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Ouvrez le **propriétés de Configuration** > **l’éditeur de liens** > **général** page de propriétés.

1. Modifier le **fichier de sortie** propriété. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Consultez <xref:Microsoft.VisualStudio.VCProjectEngine.VCLinkerTool.OutputFile%2A>.

## <a name="example"></a>Exemple

La ligne de commande suivante compile et lie tous les fichiers de code source C dans le répertoire actif. Le fichier exécutable résultant est nommé PROCESS.exe et est créé dans le répertoire « C:\Users\User Name\repos\My Project\bin ».

```
CL /Fe"C:\Users\User Name\repos\My Project\bin\PROCESS" *.C
```

## <a name="example"></a>Exemple

La ligne de commande suivante crée un fichier exécutable dans `C:\BIN` portant le même nom de base que le premier fichier source dans le répertoire actif :

```
CL /FeC:\BIN\ *.C
```

## <a name="see-also"></a>Voir aussi

[Options du fichier de sortie (/F)](output-file-f-options.md)<br/>
[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[Spécification du nom de chemin](specifying-the-pathname.md)<br/>
