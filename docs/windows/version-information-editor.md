---
title: Éditeur d’informations surC++la version ()
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
ms.openlocfilehash: e68e1480d2cd9a8d8a4d862252e6eb4384a5cd68
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69513642"
---
# <a name="version-information-editor-c"></a>Éditeur d’informations surC++la version ()

Les informations sur la version sont composées de l’identification de l’entreprise et du produit, d’un numéro de version du produit, et de la notification de copyright et de marque déposée. Avec l' **éditeur d’informations sur la version**, vous créez et gérez ces données, qui sont stockées dans la ressource d’informations sur la version. La ressource d’informations sur la version n’est pas requise par une application, mais elle est utile pour collecter des informations qui identifient l’application. Les informations sur la version sont également utilisées par les API d’installation.

> [!NOTE]
> La norme Windows consiste à n’avoir qu’une seule ressource de version, nommée VS_VERSION_INFO.

Une ressource d’informations sur la version a un bloc supérieur et un ou plusieurs blocs inférieurs : un bloc d’informations fixes unique en haut et un ou plusieurs blocs d’informations sur la version en bas (pour les autres langues et/ou jeux de caractères). Le bloc supérieur contient des zones numériques modifiables et des listes déroulantes sélectionnables. Les blocs inférieurs contiennent uniquement des zones de texte modifiables.

> [!NOTE]
> Lorsque vous utilisez l' **éditeur d’informations**sur la version, dans de nombreux cas, vous pouvez cliquer avec le bouton droit pour afficher un menu contextuel de commandes spécifiques à la ressource. Par exemple, si vous sélectionnez en pointant sur une entrée d’en-tête de bloc, le menu contextuel affiche les commandes **nouveau bloc d’informations sur la version** et **Supprimer les informations sur le bloc de version** .

## <a name="how-to"></a>Comment

L' **éditeur d’informations sur la version** vous permet d’activer les éléments suivants:

### <a name="to-edit-a-string-in-a-version-information-resource"></a>Pour modifier une chaîne dans une ressource d’informations sur la version

Sélectionnez l’élément une fois pour le choisir, puis à nouveau pour le modifier. Apportez les modifications directement dans la table d' **informations sur la version** ou dans la [fenêtre Propriétés](/visualstudio/ide/reference/properties-window). Les modifications que vous apportez apparaîtront aux deux emplacements.

Lorsque vous modifiez `FILEFLAGS` la clé dans l' **éditeur d’informations sur la version**, Notez que vous ne pouvez pas définir les propriétés **Debug**, **Private Build**ou **Special Build** dans la fenêtre **Propriétés** des fichiers. RC:

   - L' **éditeur d’informations sur la version** définit la propriété `#ifdef` **Debug** avec un dans le script de ressources `_DEBUG` , en fonction de l’indicateur de Build.

  - `FILEFLAGS` Si la cléaunevaleurdéfiniedanslatabled’informationssurlaversion,lapropriétéPrivateBuildcorrespondantedanslafenêtrePropriétésdelacléesttrue.`Private Build` Si la **valeur** est vide, la propriété est **false**. De même, la clé de **Build spéciale** dans la table d' **informations sur la version** est liée à la `FILEFLAGS` propriété **Special Build** de la clé.

Vous pouvez trier la séquence d’informations du bloc de chaîne en sélectionnant les en-têtes de colonne **clé** ou **valeur** . Ces en-têtes réorganisent automatiquement les informations dans la séquence sélectionnée.

### <a name="to-add-version-information-for-another-language-new-version-info-block"></a>Pour ajouter des informations de version pour une autre langue (nouveau bloc d’informations sur la version)

1. Ouvrez une ressource d’informations de version en double-cliquant dessus dans [Affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Cliquez avec le bouton droit dans la table d’informations sur la version, puis choisissez **nouveau bloc**d’informations sur la version.

   Cette commande ajoute un bloc d’informations supplémentaire à la ressource d’informations de version actuelle et ouvre ses propriétés correspondantes dans la fenêtre [Propriétés](/visualstudio/ide/reference/properties-window).

1. Dans la fenêtre **Propriétés** , sélectionnez la langue et le jeu de caractères appropriés pour votre nouveau bloc de caractères.

### <a name="to-delete-a-version-information-block"></a>Pour supprimer un bloc d’informations de version

1. Ouvrez la ressource d’informations de version en double-cliquant sur son icône dans l’ [Affichage des ressources](how-to-create-a-resource-script-file.md#create-resources).

1. Cliquez avec le bouton droit sur l’en-tête de bloc que vous souhaitez supprimer, puis choisissez **supprimer le bloc d’informations sur la version**.

   Cette commande supprime l’en-tête sélectionné et laisse intactes les autres informations sur la version. Vous ne pouvez pas annuler l’action.

### <a name="to-access-version-information-from-within-your-program"></a>Pour accéder aux informations de version à partir de votre programme

Si vous souhaitez accéder aux informations de version à partir de votre programme, utilisez les fonctions [GetFileVersionInfo](/windows/win32/api/winver/nf-winver-getfileversioninfow) et [VerQueryValue](/windows/win32/api/winver/nf-winver-verqueryvaluew) .

## <a name="requirements"></a>Configuration requise

Win32

## <a name="see-also"></a>Voir aussi

[Éditeurs de ressources](../windows/resource-editors.md)<br/>
[Menus et autres ressources](/windows/win32/menurc/resources)<br/>
[Informations sur la version (Windows)](/windows/win32/menurc/version-information)
