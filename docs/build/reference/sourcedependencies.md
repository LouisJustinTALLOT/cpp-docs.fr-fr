---
title: /sourceDependencies (dépendances au niveau de la source du rapport)
description: Guide de référence de l’option de compilateur/sourceDependencies dans Microsoft C++.
ms.date: 07/29/2020
f1_keywords:
- /sourceDependencies
helpviewer_keywords:
- /sourceDependencies compiler option
- /sourceDependencies
ms.openlocfilehash: 3198353ea7569c426a556522d6b931fe23c7f12c
ms.sourcegitcommit: f2a135d69a2a8ef1777da60c53d58fe06980c997
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/03/2020
ms.locfileid: "87528071"
---
# <a name="sourcedependencies-report-source-level-dependencies"></a>`/sourceDependencies`(Dépendances au niveau de la source du rapport)

Indique au compilateur de générer un fichier JSON qui détaille les dépendances au niveau de la source consommées pendant la compilation.

Le fichier JSON contient une liste des dépendances sources, notamment :
- Fichiers d’en-tête (en-têtes transitifs et inclus directement).
- PCH utilisé (si **`/Yu`** est spécifié).
- Les modules importés et les unités d’en-tête importés (à la fois les modules transitives et les unités d’en-tête).

## <a name="syntax"></a>Syntax

> **`/sourceDependencies`***nom du fichier*\
> **`/sourceDependencies`***répertoire*

## <a name="arguments"></a>Arguments

*extension*\
Le compilateur écrit la sortie de dépendance source dans le nom de fichier spécifié, qui peut inclure un chemin d’accès relatif ou absolu.

*Directory*\
Si l’argument est un répertoire, le compilateur génère des fichiers de dépendance source dans le répertoire spécifié. Le nom du fichier de sortie est basé sur le nom complet du fichier d’entrée, avec une *`.json`* extension ajoutée. Par exemple, si le fichier fourni au compilateur est *`main.cpp`* , le nom de fichier de sortie généré est *`main.cpp.json`* .

## <a name="remarks"></a>Remarques

L' **`/sourceDependencies`** option de compilateur est disponible à partir de Visual Studio 2019 version 16,7. Elle n’est pas activée par défaut.

Lorsque vous spécifiez l' **`/MP`** option de compilateur, nous vous recommandons **`/sourceDependencies`** d’utiliser avec un argument de répertoire. Si vous fournissez un argument de nom de fichier unique, deux instances du compilateur peuvent tenter d’ouvrir le fichier de sortie simultanément et générer une erreur. Pour plus d’informations sur **`/MP`** , consultez [ `/MP` (générer avec plusieurs processus)](mp-build-with-multiple-processes.md).

Lorsqu’une erreur de compilateur récupérable se produit, les informations de dépendance sont toujours écrites dans le fichier de sortie.

Tous les chemins d’accès aux fichiers apparaissent sous forme de chemins absolus dans la sortie.

### <a name="examples"></a>Exemples

Prenons l’exemple de code suivant :

```cpp
// main.cpp
#include "header.h"
import m;
import "other.h";

int main() { }
```

Vous pouvez utiliser avec **`/sourceDependencies`** les autres options du compilateur :

> `cl ... /sourceDependencies output.json ... main.cpp`

où `...` représente les autres options du compilateur. Cette ligne de commande génère un fichier JSON *`output.json`* dont le contenu ressemble à ce qui suit :

```JSON
{
    "Version": "1.0",
    "Data": {
        "Source": "C:\\...\\main.cpp",
        "PCH": "C:\\...\\pch.pch",
        "Includes": [
            "C:\\...\\header.h"
        ],
        "Modules": [
            "C:\\...\\m.ifc",
            "C:\\...\\other.h.ifc"
        ]
    }
}
```

Nous avons utilisé `...` pour abréger les chemins d’accès signalés ; le rapport contient les chemins d’accès absolus. Les chemins d’accès signalés dépendent de l’endroit où le compilateur trouve les dépendances. Si les résultats sont inattendus, vous souhaiterez peut-être vérifier les paramètres de chemin d’accès Include de votre projet.

### <a name="to-set-the-sourcedependencies-compiler-option-in-visual-studio"></a>Pour définir l’option du compilateur/sourceDependencies dans Visual Studio

1. Ouvrez la boîte de dialogue **pages de propriétés** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Dans la zone **options supplémentaires** , ajoutez, *`/sourceDependencies: <filename>`* puis cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

### <a name="to-set-this-compiler-option-programmatically"></a>Pour définir cette option du compilateur par programmation

- Cette option n’a pas d’équivalent programmatique.

## <a name="see-also"></a>Voir aussi

[Options du compilateur MSVC](compiler-options.md)<br/>
[Syntaxe de la ligne de commande du compilateur MSVC](compiler-command-line-syntax.md)<br/>
