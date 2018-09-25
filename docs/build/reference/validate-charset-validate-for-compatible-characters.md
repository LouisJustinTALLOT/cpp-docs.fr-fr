---
title: -validation-charset (valider les caractères compatibles) | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-tools
ms.topic: reference
f1_keywords:
- /validate-charset
- validate-charset
dev_langs:
- C++
helpviewer_keywords:
- /validate-charset compiler option
ms.assetid: 50360fd0-4d32-4a4f-95d0-53d38c12ad4c
author: corob-msft
ms.author: corob
ms.workload:
- cplusplus
ms.openlocfilehash: 698a221dadf21e6d314f5556210d84b98853757f
ms.sourcegitcommit: 92c568e9466ffd7346a4120c478c9bdea61c8756
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/24/2018
ms.locfileid: "47029526"
---
# <a name="validate-charset-validate-for-compatible-characters"></a>/ Validate-CharSet (valider les caractères compatibles)

Valide le fait que le texte du fichier source contient uniquement des caractères qui peut être représentées au format UTF-8.

## <a name="syntax"></a>Syntaxe

```
/validate-charset[-]
```

## <a name="remarks"></a>Notes

Vous pouvez utiliser la **/Validate-CharSet** option pour valider que le code source contient uniquement des caractères qui peuvent être représentés dans les deux caractères de code source et de jeu de caractères d’exécution. Cette vérification est activée automatiquement lorsque vous spécifiez **/source-CharSet**, **/Execution-CharSet**, ou **/UTF-8** options du compilateur. Vous pouvez désactiver explicitement cette vérification en spécifiant le **/ valider-charset -** option.

Par défaut, Visual Studio détecte une marque d’ordre d’octet pour déterminer si le fichier source est encodé au format Unicode, par exemple, UTF-16 ou UTF-8. Si aucune marque d’ordre d’octet n’est trouvé, il part du principe que le fichier source est encodé à l’aide de la page de codes utilisateur actuel, sauf si vous avez spécifié une page de codes à l’aide de **/UTF-8** ou **/source-CharSet** option. Visual Studio vous permet d’enregistrer votre code source C++ à l’aide des plusieurs encodages de caractères. Pour plus d’informations sur les jeux de caractères source et d’exécution, consultez [jeux de caractères](../../cpp/character-sets.md) dans la documentation du langage. Pour une liste de prise en charge les identificateurs de page de code et les noms de jeu de caractères, consultez [Code Page Identifiers](/windows/desktop/Intl/code-page-identifiers).

Visual Studio utilise UTF-8 en tant que l’encodage de caractères interne lors de la conversion entre le jeu de caractères source et le jeu de caractères d’exécution. Si un caractère dans le fichier source ne peut pas être représenté dans le jeu de caractères d’exécution, la conversion UTF-8 remplace par un point d’interrogation « ? » caractères. Le **/Validate-CharSet** option entraîne la compilation signaler un avertissement si cela se produit.

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriétés** du projet. Pour plus d’informations, consultez [Utilisation des propriétés de projet](../../ide/working-with-project-properties.md).

1. Développez le **propriétés de Configuration**, **C/C++**, **ligne de commande** dossier.

1. Dans **Options avancées**, ajoutez le **/Validate-CharSet** option et spécifiez votre encodage préféré.

1. Choisissez **OK** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[Options du compilateur](../../build/reference/compiler-options.md)<br/>
[Définition des options du compilateur](../../build/reference/setting-compiler-options.md)<br/>
[/ EXECUTION-CharSet (définir l’exécution du jeu de caractères)](../../build/reference/execution-charset-set-execution-character-set.md)<br/>
[/source-charset (Définir le jeu de caractères source)](../../build/reference/source-charset-set-source-character-set.md)<br/>
[/utf-8 (Définir les jeux de caractères sources et exécutables sur UTF-8)](../../build/reference/utf-8-set-source-and-executable-character-sets-to-utf-8.md)