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
ms.openlocfilehash: 8420feb6ddde116a24bee5333f4ef8f83ff4e0d4
ms.sourcegitcommit: 470de1337035dd33682d935b4b6c6d8b1bdb0bbb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 02/15/2019
ms.locfileid: "56320469"
---
# <a name="version-information-editor-c"></a>Éditeur d’informations (C++)

Les informations sur la version sont composées de l’identification de l’entreprise et du produit, d’un numéro de version du produit, et de la notification de copyright et de marque déposée. Avec le **informations de Version** éditeur, vous créez et conserver ces données, qui sont stockées dans la ressource d’informations de version. La ressource d’informations de version n’est pas requis par une application, mais il est utile pour collecter des informations qui identifient l’application. Les informations sur la version sont également utilisées par les API d’installation.

Une ressource d’informations sur la version a un bloc supérieur et un ou plusieurs blocs inférieurs : un bloc d’informations fixes unique en haut et un ou plusieurs blocs d’informations sur la version en bas (pour les autres langues et/ou jeux de caractères). Le bloc supérieur contient des zones numériques modifiables et des listes déroulantes sélectionnables. Les blocs inférieurs contiennent uniquement des zones de texte modifiables.

> [!NOTE]
> La norme Windows consiste à n’avoir qu’une seule ressource de version, nommée VS_VERSION_INFO.

## <a name="how-to"></a>Procédure

Le **informations de Version** éditeur vous permet de :

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Pour modifier une chaîne dans une ressource d’informations sur la version

Sélectionner l’élément une fois, puis à nouveau pour le modifier. Apportez les modifications directement dans le **informations de Version** table ou dans le [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Les modifications que vous apportez apparaîtront aux deux emplacements.

Lors de la modification la `FILEFLAGS` clé dans le **informations de Version** éditeur, vous remarquerez que vous ne pouvez pas définir le **déboguer**, **Private Build**, ou **spécial Build** propriétés (dans le **propriétés** fenêtre) pour les fichiers .rc :

- Le **informations de Version** éditeur attribue le **déboguer** propriété avec une `#ifdef` dans le script de ressources, selon le `_DEBUG` indicateur de build.

- Si le `Private Build` clé a un **valeur** définie le **informations de Version** correspondant de la table **Private Build** propriété (dans le **propriétés**  fenêtre) pour le `FILEFLAGS` clé sera **True**. Si la **Valeur** est vide, la propriété est **False**. De même, le **Special Build** clé (dans le **informations de Version** table) est liée à la **Special Build** propriété pour le `FILEFLAGS` clé.

Vous pouvez trier la séquence d’informations du bloc de chaîne en cliquant sur le **clé** ou **valeur** des en-têtes de colonnes. Ces en-têtes réorganisent automatiquement les informations dans la séquence sélectionnée.

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>Pour ajouter des informations de version pour une autre langue (nouveau bloc d’informations de version)

1. Ouvrez une ressource d’informations de version en double-cliquant dessus dans [Affichage des ressources](../windows/resource-view-window.md).

1. Cliquez avec le bouton droit dans la table d’informations de version et choisissez **Nouveau bloc d’informations sur la version** dans le menu contextuel.

   Cette commande ajoute un bloc d’informations supplémentaire à la ressource d’informations de version actuelle et ouvre ses propriétés correspondantes dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window).

1. Dans la fenêtre **Propriétés** , sélectionnez la langue et le jeu de caractères appropriés pour votre nouveau bloc de caractères.

### <a name="to-delete-a-version-information-block"></a>Pour supprimer un bloc d’informations de version

1. Ouvrez la ressource d’informations de version en double-cliquant sur son icône dans l’ [Affichage des ressources](../windows/resource-view-window.md).

1. Cliquez sur l’en-tête de bloc que vous souhaitez supprimer, puis choisissez **Supprimer le bloc d’informations sur la version** dans le menu contextuel.

   Cette commande supprime l’en-tête sélectionné et toucher le reste des informations de version. Vous ne pouvez pas annuler l’action.

### <a name="to-access-version-information-from-within-your-program"></a>Pour accéder aux informations de version à partir de votre programme

Si vous souhaitez accéder aux informations de version à partir de votre programme, utilisez les fonctions [GetFileVersionInfo](/windows/desktop/api/winver/nf-winver-getfileversioninfoa) et [VerQueryValue](/windows/desktop/api/winver/nf-winver-verqueryvaluea) .

   > [!NOTE]
   > Lors de l’utilisation du **informations de Version** éditeur, dans de nombreux cas, vous pouvez avec le bouton droit pour afficher un menu contextuel de commandes spécifiques à la ressource. Par exemple, si vous sélectionnez en pointant sur une entrée d’en-tête de bloc, le menu contextuel affiche les **nouveau bloc d’informations sur** et **supprimer bloc d’informations sur** commandes.

## <a name="requirements"></a>Spécifications

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Menus et autres ressources](https://msdn.microsoft.com/library/windows/desktop/ms632583.aspx)<br/>
[Informations sur la version (Windows)](https://msdn.microsoft.com/library/windows/desktop/ms646981.aspx)
