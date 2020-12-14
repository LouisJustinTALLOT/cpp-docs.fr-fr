---
description: En savoir plus sur:/source-charset (définir le jeu de caractères source)
title: /source-charset (définir le jeu de caractères source)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: 5ed1ea8e130dd61b4d5903570b781f36856d3e60
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97224775"
---
# <a name="source-charset-set-source-character-set"></a>/source-charset (définir le jeu de caractères source)

Vous permet de spécifier le jeu de caractères source pour votre fichier exécutable.

## <a name="syntax"></a>Syntaxe

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Arguments

**IANA_name**<br/>
Nom du jeu de caractères défini par l’IANA.

**CPID**<br/>
Identificateur de la page de codes sous la forme d’un nombre décimal.

## <a name="remarks"></a>Notes

Vous pouvez utiliser l’option **/source-charset** pour spécifier un jeu de caractères sources étendus à utiliser lorsque vos fichiers sources contiennent des caractères qui ne sont pas représentés dans le jeu de caractères sources de base. Le jeu de caractères source est l’encodage utilisé pour interpréter le texte source de votre programme dans la représentation interne utilisée comme entrée pour les phases de prétraitement avant la compilation. La représentation interne est ensuite convertie en jeu de caractères d’exécution pour stocker les valeurs de chaîne et de caractère dans l’exécutable. Vous pouvez utiliser le nom du jeu de caractères IANA ou ISO, ou un point (.) suivi d’un identificateur de page de codes décimaux de 3 à 5 chiffres pour spécifier le jeu de caractères à utiliser. Pour obtenir la liste des identificateurs de pages de codes et des noms de jeux de caractères pris en charge, consultez [identificateurs de page de codes](/windows/win32/Intl/code-page-identifiers).

Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est dans un format Unicode encodé, par exemple UTF-16 ou UTF-8. Si aucune marque d’ordre d’octet n’est trouvée, il suppose que le fichier source est encodé à l’aide de la page de codes de l’utilisateur actuel, sauf si vous spécifiez un nom de jeu de caractères ou une page de codes à l’aide de l’option **/source-charset** . Visual Studio vous permet d’enregistrer votre code source C++ à l’aide de plusieurs encodages de caractères. Pour plus d’informations sur les jeux de caractères source et d’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation du langage.

Le jeu de caractères source que vous fournissez doit mapper les caractères ASCII de 7 bits aux mêmes points de code dans votre jeu de caractères, ou de nombreuses erreurs de compilation sont susceptibles de se suivre. Votre jeu de caractères source doit également être mappé au jeu de caractères Unicode étendu encodable par UTF-8. Les caractères qui ne sont pas encodable en UTF-8 sont représentés par un substitut spécifique à l’implémentation. Le compilateur Microsoft utilise un point d’interrogation pour ces caractères.

Si vous souhaitez définir le jeu de caractères source et le jeu de caractères d’exécution sur UTF-8, vous pouvez utiliser l’option du compilateur **/UTF-8** comme raccourci. Cela équivaut à spécifier **/source-charset : UTF-8/Execution-charset : UTF-8** sur la ligne de commande. L’une de ces options active également l’option **/Validate-charset** par défaut.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le dossier **Propriétés de configuration**, **C/C++**, **ligne de commande** .

1. Dans **options supplémentaires**, ajoutez l’option **/source-charset** et spécifiez votre encodage préféré.

1. Choisissez **OK** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (définir le jeu de caractères d’exécution)](execution-charset-set-execution-character-set.md)<br/>
[/UTF-8 (définir les jeux de caractères source et exécutable sur UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (Valider les caractères compatibles)](validate-charset-validate-for-compatible-characters.md)
