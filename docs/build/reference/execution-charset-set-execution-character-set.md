---
title: /Execution-charset (définir le jeu de caractères d’exécution)
ms.date: 02/06/2019
f1_keywords:
- execution-charset
- /execution-charset
helpviewer_keywords:
- /execution-charset compiler option
- -execution-charset compiler option
ms.assetid: 0e02f487-2236-45bc-95f3-5760933a8f96
ms.openlocfilehash: 44e83524867bc8a914706e1f5b45b61bc4a48087
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69492917"
---
# <a name="execution-charset-set-execution-character-set"></a>/Execution-charset (définir le jeu de caractères d’exécution)

Vous permet de spécifier le jeu de caractères d’exécution de votre fichier exécutable.

## <a name="syntax"></a>Syntaxe

```
/execution-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Arguments

*IANA_name*<br/>
Nom du jeu de caractères défini par l’IANA.

*CPID*<br/>
Identificateur de la page de codes.

## <a name="remarks"></a>Notes

Vous pouvez utiliser l’option **/Execution-charset** pour spécifier un jeu de caractères d’exécution. Le jeu de caractères d’exécution est l’encodage utilisé pour le texte de votre programme qui est entré dans la phase de compilation après toutes les étapes de prétraitement. Ce jeu de caractères est utilisé pour la représentation interne des littéraux de chaîne ou de caractère dans le code compilé. Définissez cette option pour spécifier le jeu de caractères d’exécution étendu à utiliser lorsque vos fichiers sources contiennent des caractères qui ne sont pas représentables dans le jeu de caractères d’exécution de base. Vous pouvez utiliser le nom du jeu de caractères IANA ou ISO, ou un point (.) suivi d’un identificateur de page de codes décimaux de 3 à 5 chiffres pour spécifier le jeu de caractères à utiliser. Pour obtenir la liste des identificateurs de pages de codes et des noms de jeux de caractères pris en charge, consultez identificateurs de [page de codes](/windows/win32/Intl/code-page-identifiers).

Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est dans un format Unicode encodé, par exemple UTF-16 ou UTF-8. Si aucune marque d’ordre d’octet n’est trouvée, il suppose que le fichier source est encodé à l’aide de la page de codes de l’utilisateur actuel, à moins que vous ayez spécifié un nom de jeu de caractères ou une page de codes à l’aide de l’option **/source-charset** ou **/UTF-8** . Visual Studio vous permet d’enregistrer votre C++ code source à l’aide de plusieurs encodages de caractères. Pour plus d’informations sur les jeux de caractères source et d’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation du langage.

Si vous souhaitez définir le jeu de caractères source et le jeu de caractères d’exécution sur UTF-8, vous pouvez utiliser l’option du compilateur **/UTF-8** comme raccourci. Cela équivaut à spécifier **/source-charset: UTF-8/Execution-charset: UTF-8** sur la ligne de commande. L’une de ces options active également l’option **/Validate-charset** par défaut.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le dossier **Propriétés de configuration**, **CC++/** , ligne de **commande** .

1. Dans **options supplémentaires**, ajoutez l’option **/Execution-charset** et spécifiez votre encodage préféré.

1. Choisissez **OK** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/source-charset (Définir le jeu de caractères source)](source-charset-set-source-character-set.md)<br/>
[/utf-8 (Définir les jeux de caractères sources et exécutables sur UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (Valider les caractères compatibles)](validate-charset-validate-for-compatible-characters.md)
