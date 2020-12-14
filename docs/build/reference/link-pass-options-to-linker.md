---
description: En savoir plus sur:/Link (passer des options à l’éditeur de liens)
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
ms.openlocfilehash: 3617a005e6adbc41a589606aa145712fa2df442d
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97199491"
---
# <a name="link-pass-options-to-linker"></a>/link (Passer des options à l'Éditeur de liens)

Passe une ou plusieurs options de l’éditeur de liens à l’éditeur de liens.

## <a name="syntax"></a>Syntaxe

>  *éditeur de liens/Link-options*

## <a name="arguments"></a>Arguments

*éditeur de liens-options*<br/>
Option ou options de l’éditeur de liens à passer à l’éditeur de liens.

## <a name="remarks"></a>Notes

L’option **/Link** et ses options de l’éditeur de liens doivent apparaître après tous les noms de fichiers et les options CL. Un espace est requis entre **/Link** et toutes les options de l’éditeur de liens. Pour plus d’informations, consultez Référence de l' [éditeur de liens MSVC](linking.md).

## <a name="example"></a>Exemple

Cet exemple de ligne de commande compile *Hello. cpp* et le lie au fichier objet existant. *obj*. Il passe ensuite une commande **/version** supplémentaire à l’éditeur de liens :

`cl /W4 /EHsc hello.cpp there.obj /link /VERSION:3.14`

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

L’IDE envoie normalement des commandes distinctes pour compiler et lier votre code. Vous pouvez définir les options de l’éditeur de liens dans les pages de propriétés de votre projet.

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez le dossier de l’éditeur de liens **Propriétés de configuration**  >   .

1. Modifiez une ou plusieurs propriétés. Choisissez **OK** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Cette option du compilateur ne peut pas être modifiée par programmation.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)
