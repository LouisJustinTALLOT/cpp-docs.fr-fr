---
title: Éditeur d’informations (C++)
ms.date: 02/14/2019
f1_keywords:
- vc.editors.version.F1
- vc.editors.version
helpviewer_keywords:
- Version Information editor [C++], about Version Information editor
- editors, Version Information
- resource editors [C++], Version Information editor
- version information resources [C++]
- resources [C++], editing version information
- languages, version information
- New Version Info Block
- blocks, adding
- resources [C++], adding version information
- version information, adding for languages
- blocks, deleting
- version information, deleting blocks
- resources [C++], deleting version information
- VerQueryValue
- version information, accessing from within programs
- GetFileVersionInfo
- version information
ms.assetid: 772e6f19-f765-4cec-9521-0ad3eeb99f9b
ms.openlocfilehash: 8382371acfd423f8c6864e816b0357e3ef11718e
ms.sourcegitcommit: e06648107065f3dea35f40c1ae5999391087b80b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/01/2019
ms.locfileid: "57210976"
---
# <a name="version-information-editor-c"></a>Éditeur d’informations (C++)

Les informations sur la version sont composées de l’identification de l’entreprise et du produit, d’un numéro de version du produit, et de la notification de copyright et de marque déposée. Avec le **Éditeur d’informations sur Version**, vous créez et gérez ces données, qui sont stockées dans la ressource d’informations de version. La ressource d’informations de version n’est pas requis par une application, mais il est utile pour collecter des informations qui identifient l’application. Les informations sur la version sont également utilisées par les API d’installation.

> [!NOTE]
> La norme Windows consiste à n’avoir qu’une seule ressource de version, nommée VS_VERSION_INFO.

Une ressource d’informations sur la version a un bloc supérieur et un ou plusieurs blocs inférieurs : un bloc d’informations fixes unique en haut et un ou plusieurs blocs d’informations sur la version en bas (pour les autres langues et/ou jeux de caractères). Le bloc supérieur contient des zones numériques modifiables et des listes déroulantes sélectionnables. Les blocs inférieurs contiennent uniquement des zones de texte modifiables.

> [!NOTE]
> Lors de l’utilisation du **Éditeur d’informations sur Version**, dans de nombreux cas vous pouvez avec le bouton droit pour afficher un menu contextuel de commandes spécifiques à la ressource. Par exemple, si vous sélectionnez en pointant sur une entrée d’en-tête de bloc, le menu contextuel affiche les **nouveau bloc d’informations sur** et **supprimer bloc d’informations sur** commandes.

## <a name="how-to"></a>Comment

Le **Éditeur d’informations sur Version** vous permet de :

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Pour modifier une chaîne dans une ressource d’informations sur la version

Sélectionner l’élément une fois, puis à nouveau pour le modifier. Apporter des modifications directement dans le **informations de Version** table ou dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Les modifications que vous apportez apparaîtront aux deux emplacements.

Lorsque vous modifiez le `FILEFLAGS` clé dans le **Éditeur d’informations sur**, que vous ne pouvez pas définir le **déboguer**, **Private Build**, ou **Special Build**  propriétés dans le **propriétés** fenêtre pour les fichiers .rc :

   - Le **Éditeur d’informations sur** définit le **déboguer** propriété avec une `#ifdef` dans le script de ressources, selon le `_DEBUG` indicateur de build.

  - Si le `Private Build` clé a un **valeur** définie le **informations de Version** correspondant de la table **Private Build** propriété dans le **propriétés**  fenêtre pour le `FILEFLAGS` clé sera **True**. Si **valeur** est vide, la propriété sera **False**. De même, le **Special Build** clé dans le **informations de Version** table est liée à la **Special Build** propriété pour le `FILEFLAGS` clé.

Vous pouvez trier la séquence d’informations du bloc de chaîne en sélectionnant le **clé** ou **valeur** des en-têtes de colonnes. Ces en-têtes réorganisent automatiquement les informations dans la séquence sélectionnée.

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>Pour ajouter des informations de version pour une autre langue (nouveau bloc d’informations de version)

1. Ouvrez une ressource d’informations de version en double-cliquant dessus dans [Affichage des ressources](../windows/resource-view-window.md).

1. Avec le bouton droit dans la table d’informations de version et choisissez **nouveau bloc d’informations de Version**.

   Cette commande ajoute un bloc d’informations supplémentaire à la ressource d’informations de version actuelle et ouvre ses propriétés correspondantes dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window).

1. Dans la fenêtre **Propriétés** , sélectionnez la langue et le jeu de caractères appropriés pour votre nouveau bloc de caractères.

### <a name="to-delete-a-version-information-block"></a>Pour supprimer un bloc d’informations de version

1. Ouvrez la ressource d’informations de version en double-cliquant sur son icône dans l’ [Affichage des ressources](../windows/resource-view-window.md).

1. Cliquez sur l’en-tête de bloc que vous souhaitez supprimer, puis sélectionnez **supprimer le bloc d’informations de Version**.

   Cette commande supprime l’en-tête sélectionné et toucher le reste des informations de version. Vous ne pouvez pas annuler l’action.

### <a name="to-access-version-information-from-within-your-program"></a>Pour accéder aux informations de version à partir de votre programme

Si vous souhaitez accéder aux informations de version à partir de votre programme, utilisez les fonctions [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) et [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) .

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
<!--
[Menus and Other Resources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Version Information (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)-->
