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
ms.openlocfilehash: 2a3ff3d89c809f57ea3ddbd70d5664fc8d13cec4
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320820"
---
# <a name="binary-editor-c"></a>Éditeur binaire (C++)

> [!WARNING]
> Le **éditeur binaire** n’est pas disponible dans les éditions Express.

L’éditeur binaire vous permet de modifier n’importe quelle ressource au niveau binaire au format hexadécimal ou ASCII. Vous pouvez également utiliser la [commande Rechercher](/visualstudio/ide/reference/find-command) pour rechercher des chaînes ASCII ou des octets hexadécimaux. Vous devez utiliser le **binaire** éditeur uniquement lorsque vous avez besoin afficher ou de légères modifications à des ressources personnalisées ou des types de ressources non pris en charge par l’environnement Visual Studio.

Pour ouvrir le **éditeur binaire**, choisissez d’abord **fichier** > **New** > **fichier** dans le menu principal, sélectionnez le fichier à modifier, puis sélectionnez la flèche à côté du **Open** bouton, puis choisissez **ouvrir avec** > **éditeur binaire**.

> [!CAUTION]
> Modifier des ressources telles que des boîtes de dialogue, des images ou des menus dans l’éditeur binaire est une opération dangereuse. Une modification incorrecte peut endommager la ressource et la rendre illisible dans son éditeur natif.

![Éditeur binaire](../mfc/media/vcbinaryeditor2.gif "vcBinaryEditor2")<br/>
Données binaires pour une boîte de dialogue affichée dans l’éditeur binaire

Seules certaines valeurs ASCII sont représentées dans l’éditeur binaire (0x20 à 0x7E). Les caractères étendus sont affichés sous forme de points dans la section Valeur ASCII de l’éditeur binaire (volet droit). Les caractères « imprimables » sont les valeurs ASCII comprises entre 32 et 126.

> [!TIP]
> Lors de l’utilisation du **binaire** éditeur, dans de nombreux cas, vous pouvez avec le bouton droit pour afficher un menu contextuel de commandes spécifiques à la ressource. Les commandes disponibles varient selon la cible du pointeur. Par exemple, si vous cliquez en pointant sur le **binaire** éditeur avec des valeurs hexadécimales sélectionnées, le menu contextuel affiche les **couper**, **copie**, et **coller**  commandes.

## <a name="how-to"></a>Procédure

Le **binaire** éditeur vous permet de :

### <a name="to-open-a-windows-desktop-resource-for-binary-editing"></a>Pour ouvrir une ressource de bureau Windows pour l’édition binaire

1. Dans [Affichage des ressources](../windows/resource-view-window.md), sélectionnez le fichier de ressources que vous souhaitez modifier.

1. Cliquez avec le bouton droit sur la ressource et cliquez sur **Ouvrir au format binaire** dans le menu contextuel.

   > [!NOTE]
   > Si vous utilisez le [affichage des ressources](../windows/resource-view-window.md) fenêtre pour ouvrir une ressource ayant un format que Visual Studio ne reconnaît pas (comme RCDATA ou une ressource personnalisée), la ressource s’ouvre automatiquement dans le **binaire** éditeur.

### <a name="to-open-a-managed-resource-for-binary-editing"></a>Pour ouvrir une ressource managée pour l’édition binaire

1. Dans **l’Explorateur de solutions**, sélectionnez le fichier de ressources que vous souhaitez modifier.

1. Cliquez avec le bouton droit sur la ressource et choisissez **Ouvrir avec** dans le menu contextuel.

1. Dans la boîte de dialogue **Ouvrir avec** , sélectionnez **Éditeur binaire**.

   > [!NOTE]
   > Vous pouvez utiliser l’ [éditeur d’images](../windows/image-editor-for-icons.md) et l’ [éditeur binaire](binary-editor.md) pour travailler avec des fichiers de ressources dans des projets managés. Toutes les ressources managées que vous souhaitez modifier doivent être liées. Les éditeurs de ressources Visual Studio ne prennent pas en charge la modification des ressources incorporées.

> [!NOTE]
> Si vous souhaitez utiliser le **binaire** éditeur sur une ressource déjà en cours de modification dans une autre fenêtre d’éditeur, fermez l’autre fenêtre d’éditeur tout d’abord.

### <a name="to-edit-a-resource"></a>Pour modifier une ressource

1. Sélectionnez l’octet que vous souhaitez modifier.

   Le **onglet** touche déplace le focus entre les sections hexadécimale et ASCII de la **binaire** éditeur. Vous pouvez utiliser la **PG.préc** et **PG.suiv** clés pour vous déplacer dans l’écran d’une ressource à la fois.

1. Tapez la nouvelle valeur.

   La valeur change immédiatement dans à la fois les sections hexadécimale et ASCII et le focus passe à la valeur suivante dans la ligne.

   > [!NOTE]
   > Le **binaire** éditeur accepte les modifications automatiquement lorsque vous fermez l’éditeur.

### <a name="to-find-binary-data"></a>Pour rechercher des données binaires

Vous pouvez rechercher des chaînes ASCII ou des octets hexadécimaux. Par exemple, pour rechercher « Hello », vous pouvez rechercher pour soit la chaîne « Hello » ou « 48 65 6C 6C 6F » (l’équivalent hexadécimal).

1. À partir de la **modifier** menu, choisissez [trouver](/visualstudio/ide/reference/find-command).

1. Dans le **rechercher** zone, sélectionnez une chaîne de recherche précédente à partir de la liste déroulante ou tapez les données que vous souhaitez rechercher.

1. Sélectionnez un de la **trouver** options et choisissez **suivant**.

### <a name="to-create-a-new-custom-or-data-resource"></a>Pour créer une ressource personnalisée ou une ressource de données

Vous pouvez créer une nouvelle ressource personnalisée ou de données en plaçant la ressource dans un fichier distinct à l’aide de la syntaxe de fichier de script (.rc) de ressource normale, puis en incluant ce fichier en double-cliquant sur votre projet dans **l’Explorateur de solutions** et en cliquant sur  **Inclut des ressources** dans le menu contextuel.

1. [Créez un fichier .rc](../windows/how-to-create-a-resource-script-file.md) qui contient la ressource personnalisée ou de données.

   Vous pouvez taper des données personnalisées dans un fichier .rc en tant que chaînes entre guillemets terminées par un caractère Null, ou sous forme d’entiers au format octal, hexadécimal ou décimal.

1. Dans l’ **Explorateur de solutions**, cliquez sur le fichier .rc de votre projet, puis sur **Include des ressources** dans le menu contextuel.

1. Dans le **Directives de compilation** , tapez un `#include` instruction qui fournit le nom du fichier contenant la ressource personnalisée. Exemple :

    ```cpp
    #include mydata.rc
    ```

   Assurez-vous que la syntaxe et l’orthographe de ce que vous tapez sont correctes. Le contenu de la zone **Directives de compilation** est inséré dans le fichier de script de ressources exactement comme vous l’avez tapé.

1. Sélectionnez **OK** pour enregistrer vos modifications.

Une autre façon de créer une ressource personnalisée consiste à importer un fichier externe en tant que ressource personnalisée. Pour plus d’informations, consultez [Importation et exportation de ressources](../windows/how-to-import-and-export-resources.md).

> [!NOTE]
> Création de nouvelles ressources personnalisée ou de données nécessite Win32.

## <a name="requirements"></a>Spécifications

Aucun.

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)