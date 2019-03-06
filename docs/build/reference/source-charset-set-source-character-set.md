---
title: / source-CharSet (définir jeu de caractères Source)
ms.date: 02/06/2019
f1_keywords:
- source-charset
- /source-charset
helpviewer_keywords:
- /execution-charset compiler option
ms.assetid: d3c5bf7f-526d-4ee4-acc5-c1a02a4fc481
ms.openlocfilehash: ec5ac314f73c49b47f4132583d7651681b6b0545
ms.sourcegitcommit: bff17488ac5538b8eaac57156a4d6f06b37d6b7f
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/05/2019
ms.locfileid: "57413054"
---
# <a name="source-charset-set-source-character-set"></a>/ source-CharSet (définir jeu de caractères Source)

Vous permet de spécifier la source jeu de caractères pour votre fichier exécutable.

## <a name="syntax"></a>Syntaxe

```
/source-charset:[IANA_name|.CPID]
```

## <a name="arguments"></a>Arguments

**IANA_name**<br/>
Nom du jeu de caractères défini par l’IANA.

**CPID**<br/>
Identificateur de la page de code comme un nombre décimal.

## <a name="remarks"></a>Notes

Vous pouvez utiliser la **/source-CharSet** option pour spécifier un caractère étendu source définie à utiliser lors de vos fichiers sources incluent des caractères qui ne sont pas représentés dans le jeu de caractères sources de base. Le jeu de caractères source est l’encodage utilisé pour interpréter le texte de la source de votre programme dans la représentation interne utilisée comme entrée pour les phases de prétraitement avant la compilation. La représentation interne est ensuite convertie en le jeu de caractères d’exécution pour stocker les valeurs de chaîne et de caractère dans le fichier exécutable. Vous pouvez utiliser soit l’IANA ou nom de jeu de caractères ISO ou un point (.) suivi d’un identificateur de page de code décimal de 3 à 5 chiffres pour spécifier le jeu de caractères à utiliser. Pour une liste de prise en charge les identificateurs de page de code et les noms de jeu de caractères, consultez [Code Page Identifiers](/windows/desktop/Intl/code-page-identifiers).

Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est encodé au format Unicode, par exemple, UTF-16 ou UTF-8. Si aucune marque d’ordre d’octet n’est trouvé, il part du principe que le fichier source est encodé à l’aide de la page de codes utilisateur actuel, sauf si vous spécifiez un jeu de caractères nom ou page de codes à l’aide de la **/source-CharSet** option. Visual Studio vous permet d’enregistrer votre code source C++ à l’aide des plusieurs encodages de caractères. Pour plus d’informations sur les jeux de caractères source et d’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation du langage.

Le jeu de caractères source que vous fournissez doit mapper les caractères ASCII 7 bits sur les mêmes points de code dans votre jeu de caractères ou de nombreuses erreurs de compilation sont susceptibles de suivre. Votre jeu de caractères source doit également être mappable au jeu puissent être codés en UTF-8 de caractères Unicode étendus. Les caractères qui ne sont pas puissent être codés en UTF-8 sont représentés par un spécifique à l’implémentation de substitution. Le compilateur Microsoft utilise un point d’interrogation pour ces caractères.

Si vous souhaitez définir le jeu de caractères source et le jeu de caractères d’exécution au format UTF-8, vous pouvez utiliser la **/UTF-8** option du compilateur sous forme de raccourci. Il est équivalent à la spécification **/source-charset:utf-/execution 8-charset:utf-8** sur la ligne de commande. Aucune de ces options également permet la **/Validate-CharSet** option par défaut.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le **propriétés de Configuration**, **C/C++**, **ligne de commande** dossier.

1. Dans **des Options supplémentaires**, ajoutez le **/source-CharSet** option et spécifiez votre encodage préféré.

1. Choisissez **OK** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[/ EXECUTION-CharSet (définir l’exécution du jeu de caractères)](../../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/utf-8 (Définir les jeux de caractères sources et exécutables sur UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)<br/>
[/validate-charset (Valider les caractères compatibles)](../../build/reference/validate-charset-validate-for-compatible-characters.md)
