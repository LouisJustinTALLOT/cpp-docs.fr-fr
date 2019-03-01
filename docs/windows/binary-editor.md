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
ms.openlocfilehash: 420c5ecf44f8e8b264d9eafd93de58c0db3bedf4
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210716"
---
# <a name="binary-editor-c"></a>Éditeur binaire (C++)

> [!CAUTION]
> Modification des ressources telles que les boîtes de dialogue, des images ou des menus dans le **éditeur binaire** est dangereux. Une modification incorrecte peut endommager la ressource et la rendre illisible dans son éditeur natif.

Le **éditeur binaire** permet de modifier n’importe quelle ressource au niveau binaire au format hexadécimal ou ASCII. Vous pouvez également utiliser la [commande Rechercher](/visualstudio/ide/reference/find-command) pour rechercher des chaînes ASCII ou des octets hexadécimaux. Utilisez le **éditeur binaire** uniquement lorsque vous avez besoin afficher ou de légères modifications à des ressources personnalisées ou des types de ressources non pris en charge par l’environnement Visual Studio.

Pour ouvrir le **éditeur binaire** sur un nouveau fichier, accédez au menu **fichier** > **New** > **fichier**, sélectionnez le type de fichier à modifier, puis sélectionnez la flèche à côté du **Open** bouton, puis choisissez **ouvrir avec** > **éditeur binaire**.

Pour ouvrir le **éditeur binaire** sur un fichier existant, accédez au menu **fichier** > **ouvrir** > **fichier**, sélectionnez le fichier à modifier, puis sélectionnez la flèche à côté du **Open** bouton, puis choisissez **ouvrir avec** > **éditeur binaire**.

   ![Éditeur binaire](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
   Données binaires pour une boîte de dialogue affichée dans le **éditeur binaire**

Seules certaines valeurs ASCII sont représentées dans le **éditeur binaire** (0 x 20 à 0x7E). Les caractères étendus sont affichés sous forme de points dans la section de valeur ASCII panneau droit de la **éditeur binaire**. Les caractères imprimables sont des valeurs ASCII comprises entre 32 et 126.

> [!TIP]
> Lors de l’utilisation du **éditeur binaire**, dans de nombreux cas vous pouvez avec le bouton droit pour afficher un menu contextuel de commandes spécifiques à la ressource. Les commandes disponibles varient selon la cible du pointeur. Par exemple, si vous cliquez en pointant sur le **éditeur binaire** avec des valeurs hexadécimales sélectionnées, le menu contextuel affiche les **couper**, **copie**, et **coller**  commandes.

Le **éditeur binaire** n’est pas disponible dans les éditions Express.

## <a name="how-to"></a>Comment

Le **éditeur binaire** vous permet de :

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Pour ouvrir une ressource de bureau Windows pour l’édition binaire

1. Dans [Affichage des ressources](../windows/resource-view-window.md), sélectionnez le fichier de ressources que vous souhaitez modifier.

1. Cliquez sur la ressource et sélectionnez **Open Data binaire**.

> [!NOTE]
> Si vous utilisez le [affichage des ressources](../windows/resource-view-window.md) fenêtre pour ouvrir une ressource ayant un format que Visual Studio ne reconnaît pas, comme RCDATA ou une ressource personnalisée, la ressource s’ouvre automatiquement dans le **éditeur binaire**.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>Pour ouvrir une ressource managée pour l’édition binaire

1. Dans **l’Explorateur de solutions**, sélectionnez le fichier de ressources que vous souhaitez modifier.

1. Cliquez sur la ressource et sélectionnez **ouvrir avec**.

1. Dans la boîte de dialogue **Ouvrir avec** , sélectionnez **Éditeur binaire**.

> [!NOTE]
> Vous pouvez utiliser la [Éditeur d’images](../windows/image-editor-for-icons.md) et **éditeur binaire** pour travailler avec des fichiers de ressources dans les projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

### <a name="to-edit-a-resource"></a>Pour modifier une ressource

> [!NOTE]
> Si vous souhaitez utiliser le **éditeur binaire** sur une ressource déjà en cours de modification dans une autre fenêtre d’éditeur, fermez tout d’abord l’autre fenêtre d’éditeur.

1. Sélectionnez l’octet que vous souhaitez modifier.

   Le **onglet** touche déplace le focus entre les sections hexadécimale et ASCII de la **éditeur binaire**. Vous pouvez utiliser la **PG.préc** et **PG.suiv** clés pour vous déplacer dans l’écran d’une ressource à la fois.

1. Tapez la nouvelle valeur.

   La valeur change immédiatement dans à la fois les sections hexadécimale et ASCII et le focus passe à la valeur suivante dans la ligne.

> [!NOTE]
> Le **éditeur binaire** accepte les modifications automatiquement lorsque vous fermez l’éditeur.

### <a name="to-find-binary-data"></a>Pour rechercher des données binaires

Vous pouvez rechercher des chaînes ASCII ou des octets hexadécimaux. Par exemple, pour rechercher *Hello*, vous pouvez rechercher la chaîne *Hello* ou sa valeur hexadécimale, *48 65 6C 6C 6F*.

1. À partir de la **modifier** menu, choisissez [trouver](/visualstudio/ide/reference/find-command).

1. Dans le **rechercher** zone, sélectionnez une chaîne de recherche précédente à partir de la liste déroulante ou tapez les données que vous souhaitez rechercher.

1. Sélectionnez un de la **trouver** options et choisissez **suivant**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Pour créer une ressource personnalisée ou une ressource de données

Vous pouvez créer une nouvelle ressource personnalisée ou de données en plaçant la ressource dans un fichier distinct à l’aide de la syntaxe de fichier de script (.rc) de ressource normale, puis en incluant ce fichier en double-cliquant sur votre projet dans **l’Explorateur de solutions** et en sélectionnant  **Include des ressources**.

1. [Créez un fichier .rc](../windows/how-to-create-a-resource-script-file.md) qui contient la ressource personnalisée ou de données.

   Vous pouvez taper des données personnalisées dans un fichier .rc en tant que chaînes entre guillemets terminées par un caractère Null, ou sous forme d’entiers au format octal, hexadécimal ou décimal.

1. Dans **l’Explorateur de solutions**, cliquez sur le fichier .rc du projet et sélectionnez **Include des ressources**.

1. Dans le **Directives de compilation** , tapez un `#include` instruction qui fournit le nom du fichier contenant la ressource personnalisée, par exemple :

    ```cpp
    #include mydata.rc
    ```

   Assurez-vous que la syntaxe et l’orthographe de ce que vous tapez sont correctes. Le contenu de la **Directives de compilation** boîte est inséré dans le fichier de script de ressources exactement comme vous les tapez.

1. Sélectionnez **OK** pour enregistrer vos modifications.

Une autre façon de créer une ressource personnalisée consiste à importer un fichier externe en tant que ressource personnalisée, consultez [Comment : Gérer les ressources](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> Création de nouvelles ressources personnalisée ou de données nécessite Win32.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)