---
title: Éditeur binaire (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.binary.F1
- vc.editors.binary
helpviewer_keywords:
- editors, Binary
- resources [C++], editing
- resource editors [C++], Binary editor
- Binary editor
- binary data, editing
- resources [C++], opening for binary editing
- binary data
- hexadecimal bytes in binary data
- strings [C++], searching for
- file searches [C++]
- binary data, finding
- ASCII characters, finding in binary data
- custom resources [C++]
- data resources [C++]
- resources [C++], creating
ms.assetid: 2483c48b-1252-4dbc-826b-82e6c1a0e9cb
ms.openlocfilehash: 591a6714f1adabb30fda446cad0e79e2c28c30ad
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80215239"
---
# <a name="binary-editor-c"></a>Éditeur binaire (C++)

> [!CAUTION]
> La modification de ressources telles que des boîtes de dialogue, des images ou des menus dans l' **Éditeur binaire** est dangereuse. Une modification incorrecte peut endommager la ressource et la rendre illisible dans son éditeur natif.

L' **Éditeur binaire** vous permet de modifier n’importe quelle ressource au niveau binaire au format hexadécimal ou ASCII. Vous pouvez également utiliser la [commande Rechercher](/visualstudio/ide/reference/find-command) pour rechercher des chaînes ASCII ou des octets hexadécimaux. Utilisez l' **Éditeur binaire** uniquement lorsque vous avez besoin d’afficher ou d’apporter des modifications mineures à des ressources personnalisées ou à des types de ressources non pris en charge par l’environnement Visual Studio. L' **Éditeur binaire** n’est pas disponible dans les éditions Express.

- Pour ouvrir l' **Éditeur binaire** sur un nouveau fichier, accédez à **fichier** de menu **New** > nouveau **fichier**de > , sélectionnez le type de fichier à modifier, puis sélectionnez la flèche déroulante en regard du bouton **ouvrir** et choisissez **Ouvrir avec** > **Éditeur binaire**.

- Pour ouvrir l' **Éditeur binaire** sur un fichier existant, accédez au menu **fichier** > **ouvrez** > **fichier**, sélectionnez le fichier que vous souhaitez modifier, puis sélectionnez la flèche déroulante en regard du bouton **ouvrir** et choisissez **Ouvrir avec** > **Éditeur binaire**.

   ![Binary Editor](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   Données binaires pour une boîte de dialogue affichée dans l' **Éditeur binaire**

Seules certaines valeurs ASCII sont représentées dans l' **Éditeur binaire** (0X20 à 0x7E). Les caractères étendus sont affichés sous forme de points dans la section valeur ASCII du volet droit de l' **Éditeur binaire**. Les caractères imprimables sont des valeurs ASCII 32 à 126.

> [!TIP]
> Lorsque vous utilisez l' **Éditeur binaire**, dans de nombreux cas, vous pouvez cliquer avec le bouton droit pour afficher un menu contextuel de commandes spécifiques à la ressource. Les commandes disponibles varient selon la cible du pointeur. Par exemple, si vous cliquez avec le bouton droit de la souris en pointant sur l' **Éditeur binaire** avec des valeurs hexadécimales sélectionnées, le menu contextuel affiche les commandes **couper**, **copier**et **coller** .

## <a name="how-to"></a>Procédure

L' **Éditeur binaire** vous permet d’activer les éléments suivants :

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Pour ouvrir une ressource de bureau Windows pour l’édition binaire

1. Dans [Affichage des ressources](how-to-create-a-resource-script-file.md#create-resources), sélectionnez le fichier de ressources que vous souhaitez modifier.

1. Cliquez avec le bouton droit sur la ressource et sélectionnez **ouvrir les données binaires**.

> [!NOTE]
> Si vous utilisez la fenêtre **affichage des ressources** pour ouvrir une ressource ayant un format que Visual Studio ne reconnaît pas, comme RCDATA ou une ressource personnalisée, la ressource est automatiquement ouverte dans l' **Éditeur binaire**.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>Pour ouvrir une ressource managée pour l’édition binaire

1. Dans **Explorateur de solutions**, sélectionnez le fichier de ressources spécifique que vous souhaitez modifier.

1. Cliquez avec le bouton droit sur la ressource, puis sélectionnez **Ouvrir avec**.

1. Dans la boîte de dialogue **Ouvrir avec** , sélectionnez **Éditeur binaire**.

> [!NOTE]
> Vous pouvez utiliser l' [éditeur d’images](../windows/image-editor-for-icons.md) et l' **Éditeur binaire** pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

### <a name="to-edit-a-resource"></a>Pour modifier une ressource

Si vous souhaitez utiliser l' **Éditeur binaire** sur une ressource déjà en cours de modification dans une autre fenêtre d’éditeur, fermez d’abord l’autre fenêtre de l’éditeur.

1. Sélectionnez l’octet que vous souhaitez modifier.

   La touche **Tab** déplace le focus entre les sections hexadécimale et ASCII de l' **Éditeur binaire**. Vous pouvez utiliser les touches **PG** . **suiv et PG. suiv** . pour vous déplacer dans la ressource un écran à la fois.

1. Tapez la nouvelle valeur.

   La valeur change immédiatement dans les sections hexadécimale et ASCII et le focus passe à la valeur suivante dans la ligne.

> [!NOTE]
> L' **Éditeur binaire** accepte les modifications automatiquement quand vous fermez l’éditeur.

### <a name="to-find-binary-data"></a>Pour rechercher des données binaires

Vous pouvez rechercher des chaînes ASCII ou des octets hexadécimaux. Par exemple, pour rechercher *Hello*, vous pouvez rechercher la chaîne *Hello* ou sa valeur hexadécimale, *48 65 6C 6C 6F*.

1. Accédez au menu **modifier** > [Rechercher](/visualstudio/ide/reference/find-command).

1. Dans la zone **Rechercher** , sélectionnez une chaîne de recherche précédente dans la liste déroulante ou tapez les données que vous souhaitez rechercher.

1. Sélectionnez l’une des options de **recherche** , puis choisissez **suivant**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Pour créer une ressource personnalisée ou une ressource de données

Vous pouvez créer une ressource personnalisée ou une ressource de données en plaçant la ressource dans un fichier distinct à l’aide de la syntaxe de fichier de script de ressources normal (. RC), puis en incluant ce fichier en cliquant avec le bouton droit sur votre projet dans **Explorateur de solutions** et en sélectionnant **inclure les ressources**.

1. [Créez un fichier .rc](../windows/how-to-create-a-resource-script-file.md) qui contient la ressource personnalisée ou de données.

   Vous pouvez taper des données personnalisées dans un fichier .rc en tant que chaînes entre guillemets terminées par un caractère Null, ou sous forme d’entiers au format octal, hexadécimal ou décimal.

1. Dans **Explorateur de solutions**, cliquez avec le bouton droit sur le fichier. RC de votre projet, puis sélectionnez **include des ressources**.

1. Dans la zone **directives au moment** de la compilation, tapez une instruction `#include` qui donne le nom du fichier contenant votre ressource personnalisée, par exemple :

    ```cpp
    #include mydata.rc
    ```

   Assurez-vous que la syntaxe et l’orthographe de ce que vous tapez sont correctes. Le contenu de la zone **directives au moment** de la compilation est inséré dans le fichier de script de ressources exactement à mesure que vous les tapez.

1. Sélectionnez **OK** pour enregistrer vos modifications.

Une autre façon de créer une ressource personnalisée consiste à importer un fichier externe en tant que ressource personnalisée, consultez [How to : Manage Resources](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> La création de nouvelles ressources personnalisées ou de données requiert Win32.

## <a name="requirements"></a>Spécifications

None

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)
