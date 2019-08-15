---
title: /UTF-8 (définir les jeux de caractères source et exécutable sur UTF-8)
ms.date: 11/04/2016
f1_keywords:
- /utf-8
helpviewer_keywords:
- /utf-8 compiler option
ms.assetid: f0e1f3cb-6cae-46eb-9483-04ed13d9b504
ms.openlocfilehash: 1ff0f23ad0758642c73b1b35d6d4dd1be20899cb
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498176"
---
# <a name="utf-8-set-source-and-executable-character-sets-to-utf-8"></a>/UTF-8 (définir les jeux de caractères source et exécutable sur UTF-8)

Spécifie le jeu de caractères source et le jeu de caractères d’exécution au format UTF-8.

## <a name="syntax"></a>Syntaxe

```
/utf-8
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser l’option **/UTF-8** pour spécifier les jeux de caractères source et d’exécution comme étant encodés à l’aide d’UTF-8. Cela équivaut à spécifier **/source-charset: UTF-8/Execution-charset: UTF-8** sur la ligne de commande. L’une de ces options active également l’option **/Validate-charset** par défaut. Pour obtenir la liste des identificateurs de pages de codes et des noms de jeux de caractères pris en charge, consultez identificateurs de [page de codes](/windows/win32/Intl/code-page-identifiers).

Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est dans un format Unicode encodé, par exemple UTF-16 ou UTF-8. Si aucune marque d’ordre d’octet n’est trouvée, il suppose que le fichier source est encodé à l’aide de la page de codes de l’utilisateur actuel, à moins que vous n’ayez spécifié une page de codes à l’aide de **/UTF-8** ou de l’option **/source-charset** . Visual Studio vous permet d’enregistrer votre C++ code source à l’aide de plusieurs encodages de caractères. Pour plus d’informations sur les jeux de caractères source et d’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation du langage.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le dossier **Propriétés de configuration**, **CC++/** , ligne de **commande** .

1. Dans **options supplémentaires**, ajoutez l’option **/UTF-8** pour spécifier l’encodage de votre choix.

1. Choisissez **OK** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (définir le jeu de caractères d’exécution)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (Définir le jeu de caractères source)](source-charset-set-source-character-set.md)<br/>
[/validate-charset (Valider les caractères compatibles)](validate-charset-validate-for-compatible-characters.md)
