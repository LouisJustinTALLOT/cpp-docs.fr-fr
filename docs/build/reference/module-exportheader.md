---
title: '/module : exportHeader (créer des unités d’en-tête)'
description: 'Utilisez l’option de compilateur/module : exportHeader pour créer des unités d’en-tête de module pour le nom d’en-tête ou les fichiers include spécifiés.'
ms.date: 09/13/2020
f1_keywords:
- /module:exportHeader
helpviewer_keywords:
- /module:exportHeader
- Create header units
ms.openlocfilehash: f0c0ce1c593df742af77aa36189df1e89de75b6b
ms.sourcegitcommit: b492516cc65120250b9ea23f96f7f63f37f99fae
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/14/2020
ms.locfileid: "90079084"
---
# <a name="moduleexportheader-create-header-units"></a>`/module:exportHeader` (Créer des unités d’en-tête)

Indique au compilateur de créer les unités d’en-tête spécifiées par les arguments d’entrée. Le compilateur génère une sortie dans des *`.ifc`* fichiers IFC ().

## <a name="syntax"></a>Syntaxe

> **`/module:exportHeader`** *`header-name`* \[...]\
> **`/module:exportHeader`** *`filename`* \[...]

### <a name="arguments"></a>Arguments

*`header-name`*\
Fichier d’en-tête à exporter. L' *`header-name`* argument doit avoir la même forme qu’un argument d’une `#include` directive.

*`filename`*\
Chemin d’accès relatif ou absolu du fichier d’en-tête à partir duquel créer une unité d’en-tête.

## <a name="remarks"></a>Notes

L' **`/module:exportHeader`** option de compilateur requiert l’activation de la prise en charge des modules expérimentaux à l’aide de l' [`/experimental:module`](experimental-module.md) option du compilateur, avec l’option [/std : c + + latest](std-specify-language-standard-version.md) . Cette option est disponible à partir de Visual Studio 2019 version 16,8.

Une **`/module:exportHeader`** option du compilateur peut spécifier autant d’arguments de nom d’en-tête que requis par votre Build. Vous n’avez pas besoin de les spécifier séparément.

Par défaut, le compilateur ne produit pas de fichier objet lorsqu’une unité d’en-tête est compilée. Pour produire un fichier objet, spécifiez l' **`/Fo`** option du compilateur. Pour plus d’informations, consultez [ `/Fo` (nom du fichier objet)](fo-object-file-name.md).

Le compilateur résout un *`header-name`* en fonction de l’ordre de recherche des répertoires Include, y compris ceux que vous spécifiez. Pour plus d’informations, consultez [ `/I` (autres répertoires Include)](i-additional-include-directories.md).

L’argument *`header-name`* doit être spécifié de la même manière qu’il s’affiche dans la source. L’argument est sensible aux règles de guillemets et `<` aux `>` opérateurs et sur la ligne de commande. La commande correctement placée dans une séquence d’échappement pour générer une unité d’en-tête telle que `<vector>` l’utilisation de l’invite de commandes VS2019 peut se présenter comme suit :

```cmd
cl ... /experimental:module /module:exportHeader "<vector>"
```

La génération d’un en-tête de projet local tel que `"utils/util.h"` peut se présenter comme suit :

```cmd
cl ... /experimental:module /module:exportHeader """util/util.h"""
```

Les règles de citation dans d’autres processeurs de ligne de commande peuvent différer.

Lorsque vous utilisez la *`header-name`* forme de **`/module:exportHeader`** , il peut s’avérer utile d’utiliser l’option complémentaire **`/module:showResolvedHeader`** . L' **`/module:showResolvedHeader`** option imprime un chemin d’accès absolu au fichier *`header-name`* dans lequel l’argument est résolu.

**`/module:exportHeader`** peut gérer plusieurs entrées à la fois, même sous **`/MP`** . Nous vous recommandons **`/module:output <directory>`** d’utiliser pour créer un fichier IFC distinct pour chaque compilation.

### <a name="examples"></a>Exemples

En-têtes donnés `"C:\util\util.h"` et `"C:\app\app.h"` , vous pouvez les exporter en tant qu' *`header-name`* arguments à l’aide de cette commande :

```cmd
cl /IC:\ /experimental:module /module:exportHeader """util/util.h""" """app/app.h""" /FoC:\obj
```

Vous pouvez les exporter en tant qu' *`filename`* arguments à l’aide de cette commande :

```cmd
cl /IC:\ /experimental:module /module:exportHeader C:\util\util.h C:\app\app.h /FoC:\obj
```

### <a name="to-set-this-compiler-option-in-the-visual-studio-development-environment"></a>Pour définir cette option du compilateur dans l'environnement de développement Visual Studio

1. Ouvrez la boîte de dialogue **Pages de propriété** du projet. Pour plus d’informations, consultez [Définir le compilateur C++ et les propriétés de build dans Visual Studio](../working-with-project-properties.md).

1. Définissez la liste déroulante de **configuration** sur **toutes les configurations**.

1. Sélectionnez la page de propriétés ligne de commande des **Propriétés de configuration**  >  **C/C++**  >  **Command Line** .

1. Modifiez la propriété **options supplémentaires** pour ajouter l' *`/module:exportHeader`* option et tous les arguments. Ensuite, cliquez sur **OK** ou sur **appliquer** pour enregistrer vos modifications.

## <a name="see-also"></a>Voir aussi

[`/experimental:module` (Activer la prise en charge des modules)](experimental-module.md)\
[`/headerUnit` (Utiliser l’unité d’en-tête IFC)](headerunit.md)\
[`/module:reference` (Utilisez le module nommé IFC)](module-reference.md)\
[`/translateInclude` (Traduire les directives include en directives Import)](translateinclude.md)
