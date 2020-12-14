---
description: En savoir plus sur:/Validate-charset (valider les caractères compatibles)
title: /validate-charset (Valider les caractères compatibles)
ms.date: 02/06/2019
f1_keywords:
- /validate-charset
- validate-charset
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
ms.openlocfilehash: bda69c59fc89aae5028543ba579ee1e0b70f67e7
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97250398"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/validate-charset (Valider les caractères compatibles)

Valide que le texte du fichier source contient uniquement des caractères pouvant être représentés en UTF-8.

## <a name="syntax"></a>Syntaxe

```
/validate-charset[-]
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser l’option **/Validate-charset** pour vérifier que le code source contient uniquement des caractères qui peuvent être représentés à la fois dans le jeu de caractères source et dans le jeu de caractères d’exécution. Cette vérification est activée automatiquement lorsque vous spécifiez les options du compilateur **/source-charset**, **/Execution-charset** ou **/UTF-8** . Vous pouvez désactiver explicitement cette vérification en spécifiant l’option **/Validate-charset-** .

Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est dans un format Unicode encodé, par exemple UTF-16 ou UTF-8. Si aucune marque d’ordre d’octet n’est trouvée, il suppose que le fichier source est encodé à l’aide de la page de codes de l’utilisateur actuel, à moins que vous n’ayez spécifié une page de codes à l’aide de **/UTF-8** ou de l’option **/source-charset** . Visual Studio vous permet d’enregistrer votre code source C++ à l’aide de plusieurs encodages de caractères. Pour plus d’informations sur les jeux de caractères source et d’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation du langage. Pour obtenir la liste des identificateurs de pages de codes et des noms de jeux de caractères pris en charge, consultez [identificateurs de page de codes](/windows/win32/Intl/code-page-identifiers).

Visual Studio utilise UTF-8 comme encodage de caractères interne lors de la conversion entre le jeu de caractères source et le jeu de caractères d’exécution. Si un caractère du fichier source ne peut pas être représenté dans le jeu de caractères d’exécution, la conversion UTF-8 remplace un caractère point d’interrogation «  ? ». Avec l’option **/Validate-charset** , la compilation signale un avertissement si cela se produit.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Développez le dossier **Propriétés de configuration**, **C/C++**, **ligne de commande** .

1. Dans **options supplémentaires**, ajoutez l’option **/Validate-charset** et spécifiez votre encodage préféré.

1. Choisissez **OK** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe Command-Line du compilateur MSVC](compiler-command-line-syntax.md)<br/>
[/Execution-charset (définir le jeu de caractères d’exécution)](execution-charset-set-execution-character-set.md)<br/>
[/source-charset (définir le jeu de caractères source)](source-charset-set-source-character-set.md)<br/>
[/UTF-8 (définir les jeux de caractères source et exécutable sur UTF-8)](utf-8-set-source-and-executable-character-sets-to-utf-8.md)
