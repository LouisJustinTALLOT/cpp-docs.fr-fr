---
title: /link (Passer des options à l'Éditeur de liens)
ms.date: 03/25/2019
f1_keywords:
- /link
helpviewer_keywords:
- /link compiler option [C++]
- pass options to linker
- link compiler option [C++]
- linker [C++], passing options to
- -link compiler option [C++]
- cl.exe compiler [C++], passing options to linker
ms.assetid: 16902a94-c094-4328-841f-3ac94ca04848
ms.openlocfilehash: ef81a6617df811660506c08434f3b65e29155794
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62290677"
---
# <a name="link-pass-options-to-linker"></a>/link (Passer des options à l'Éditeur de liens)

Passe une ou plusieurs options de l’éditeur de liens à l’éditeur de liens.

## <a name="syntax"></a>Syntaxe

> **/link** *linker-options*

## <a name="arguments"></a>Arguments

*linker-options*<br/>
L’éditeur de liens les options à passer à l’éditeur de liens.

## <a name="remarks"></a>Notes

Le **/link** option et ses options de l’éditeur de liens doivent apparaître après les noms de fichiers et les options CL. Un espace est requis entre **/link,** et `linkeroptions`. Pour plus d’informations, consultez [référence de l’éditeur de liens MSVC](linking.md).

## <a name="example"></a>Exemple

Cet exemple de ligne de commande compile *hello.cpp* et le lie au fichier objet existant *there.obj*. Il passe ensuite un autre **/VERSION** commande à l’éditeur de liens :

`cl /W4 /EHsc hello.cpp there.obj /link /VERSION:3.14`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

Normalement, l’IDE envoie des commandes distinctes pour compiler et lier votre code. Vous pouvez définir des options de l’éditeur de liens dans vos pages de propriétés de projet.

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [propriétés de compilateur et de build C++ définie dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le **propriétés de Configuration** > **l’éditeur de liens** dossier.

1. Modifier une ou plusieurs propriétés. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Cette option du compilateur ne peut pas être modifiée par programmation.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)
