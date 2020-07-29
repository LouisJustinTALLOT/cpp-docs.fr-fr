---
title: Implémentation d’une page de propriétés (ATL)
ms.date: 05/09/2019
helpviewer_keywords:
- property pages, implementing
ms.assetid: c30b67fe-ce08-4249-ae29-f3060fa8d61e
ms.openlocfilehash: 688cd337d0754fc49ede0f39fd774c9990f7c79f
ms.sourcegitcommit: 1f009ab0f2cc4a177f2d1353d5a38f164612bdb1
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 07/27/2020
ms.locfileid: "87224355"
---
# <a name="example-implementing-a-property-page"></a>Exemple : implémentation d’une page de propriétés

::: moniker range="vs-2019"

L’Assistant Page de propriétés ATL n’est pas disponible dans Visual Studio 2019 et versions ultérieures.

::: moniker-end

::: moniker range="<=vs-2017"

Cet exemple montre comment créer une page de propriétés qui affiche (et vous permet de modifier) les propriétés de l’interface [Classes de documents](../mfc/document-classes.md).

L’exemple est basé sur [l’exemple ATLPages](../overview/visual-cpp-samples.md).

Pour mettre en place cet exemple, vous allez :

- [Ajouter la classe de page de propriétés ATL](#vcconusing_the_atl_object_wizard) à l’aide de la boîte de dialogue Ajouter une classe et de l’Assistant Page de propriétés ATL.

- [Modifier la ressource de boîte de dialogue](#vcconediting_the_dialog_resource) en ajoutant des contrôles aux propriétés intéressantes de l’interface `Document`.

- [Ajouter des gestionnaires de messages](#vcconadding_message_handlers) pour que le site de la page de propriétés reste informé des modifications apportées par l’utilisateur.

- Ajouter certaines instructions `#import` et un typedef dans la section [Tâches de nettoyage](#vcconhousekeeping).

- [Substituer IPropertyPageImpl::SetObjects](#vcconoverriding_ipropertypageimpl_setobjects) pour valider les objets transmis à la page de propriétés.

- [Substituer IPropertyPageImpl::Activate](#vcconoverriding_ipropertypageimpl_activate) pour initialiser l’interface de la page de propriétés.

- [Substituer IPropertyPageImpl::Apply](#vcconoverride_ipropertypageimpl_apply) pour mettre à jour l’objet avec les dernières valeurs de propriété.

- [Afficher la page de propriétés](#vccontesting_the_property_page) en créant un objet d’assistance simple.

- [Créer une macro](#vcconcreating_a_macro) qui testera la page de propriétés.

## <a name="adding-the-atl-property-page-class"></a><a name="vcconusing_the_atl_object_wizard"></a> Ajout de la classe de page de propriétés ATL

Commencez par créer un projet ATL pour un serveur DLL appelé `ATLPages7`. Utilisez maintenant [l’Assistant Page de propriétés ATL](../atl/reference/atl-property-page-wizard.md) pour générer une page de propriétés. Renseignez le champ **Nom court** de la page de propriétés avec la valeur **DocProperties**, puis basculez sur la page **Chaînes** pour définir les éléments spécifiques de page de propriétés comme indiqué dans le tableau ci-dessous.

|Élément|Valeur|
|----------|-----------|
|Titre|TextDocument|
|Chaîne doc|VCUE TextDocument Properties|
|Helpfile|*\<blank>*|

Les valeurs que vous définissez sur cette page de l’Assistant sont envoyées au conteneur de page de propriétés lorsqu’il appelle `IPropertyPage::GetPageInfo`. Ce qu’il advient des chaînes après cette opération dépend du conteneur, mais en général, elles sont utilisées pour identifier votre page pour l’utilisateur. Le titre s’affiche généralement dans un onglet au-dessus de votre page, et la chaîne doc peut être affichée dans une barre d’état ou info-bulle (bien que le frame de propriété standard n’utilise pas cette chaîne du tout).

> [!NOTE]
> Les chaînes que vous définissez ici sont stockées en tant que ressources de chaîne dans votre projet par l’Assistant. Vous pouvez facilement modifier ces chaînes à l’aide de l’éditeur de ressources si vous avez besoin de modifier ces informations une fois que le code de votre page a été généré.

Cliquez sur **OK** pour que l’Assistant génère votre page de propriétés.

## <a name="editing-the-dialog-resource"></a><a name="vcconediting_the_dialog_resource"></a> Modification de la ressource de boîte de dialogue

Maintenant que votre page de propriétés est générée, vous devez ajouter quelques contrôles à la ressource de boîte de dialogue représentant votre page. Ajoutez un champ de modification, un contrôle de texte statique et une case à cocher, puis définissez leurs ID comme indiqué ci-dessous :

![Modification d'une ressource de boîte de dialogue](../atl/media/ppgresourcelabeled.gif "Modification d'une ressource de boîte de dialogue")

Ces contrôles sont utilisés pour afficher le nom de fichier du document et son état en lecture seule.

> [!NOTE]
> La ressource de boîte de dialogue n’inclut pas de frame ou de boutons de commande, et, contrairement à ce que vous pouvez penser, ne ressemble pas à un onglet. Ces caractéristiques sont fournies par un frame de page de propriétés tel que celui créé en appelant [OleCreatePropertyFrame](/windows/win32/api/olectl/nf-olectl-olecreatepropertyframe).

## <a name="adding-message-handlers"></a><a name="vcconadding_message_handlers"></a> Ajout de gestionnaires de messages

Avec les contrôles en place, vous pouvez ajouter des gestionnaires de messages pour mettre à jour l’état modifié de la page lorsque la valeur de l’un des contrôles change :

[!code-cpp[NVC_ATL_Windowing#73](../atl/codesnippet/cpp/example-implementing-a-property-page_1.h)]

Ce code répond aux modifications apportées au contrôle d’édition ou à la case à cocher en appelant [IPropertyPageImpl::SetDirty](../atl/reference/ipropertypageimpl-class.md#setdirty), qui informe le site de la page que la page a été modifiée. En général, le site de la page répond en activant ou désactivant un bouton **Appliquer** sur le frame de la page de propriété.

> [!NOTE]
> Dans vos propres pages de propriétés, vous avez peut-être besoin de suivre précisément quelles propriétés ont été modifiées par l’utilisateur pour éviter de mettre à jour des propriétés qui n’ont pas été modifiées. Cet exemple implémente ce code en gardant une trace des valeurs de propriété d’origine et en les comparant avec les valeurs actuelles de l’IU au moment d’appliquer les modifications.

## <a name="housekeeping"></a><a name="vcconhousekeeping"></a> Tâches de nettoyage

Maintenant, ajoutez deux instructions `#import` à DocProperties.h afin que le compilateur reconnaisse l’interface `Document` :

[!code-cpp[NVC_ATL_Windowing#74](../atl/codesnippet/cpp/example-implementing-a-property-page_2.h)]

Vous devez également faire référence à la `IPropertyPageImpl` classe de base. Ajoutez le code suivant **`typedef`** à la `CDocProperties` classe :

[!code-cpp[NVC_ATL_Windowing#75](../atl/codesnippet/cpp/example-implementing-a-property-page_3.h)]

## <a name="overriding-ipropertypageimplsetobjects"></a><a name="vcconoverriding_ipropertypageimpl_setobjects"></a> Substitution de IPropertyPageImpl::SetObjects

La première méthode `IPropertyPageImpl` que vous devez substituer est [SetObjects](../atl/reference/ipropertypageimpl-class.md#setobjects). Ici, vous allez ajouter du code pour vérifier qu’un seul objet a été transmis et qu’il prend en charge l’interface `Document` que vous attendez :

[!code-cpp[NVC_ATL_Windowing#76](../atl/codesnippet/cpp/example-implementing-a-property-page_4.h)]

> [!NOTE]
> Il est judicieux de prendre en charge un seul objet de cette page, car vous allez autoriser l’utilisateur à définir le nom de fichier de l’objet ; seul un fichier peut exister à un emplacement.

## <a name="overriding-ipropertypageimplactivate"></a><a name="vcconoverriding_ipropertypageimpl_activate"></a> Substitution de IPropertyPageImpl::Activate

L’étape suivante consiste à initialiser la page de propriétés avec les valeurs de propriété de l’objet sous-jacent lors de la création de la page.

Dans ce cas, vous devez ajouter les membres suivants à la classe, puisque vous allez également utiliser les valeurs de propriété initiales à des fins de comparaison lorsque les utilisateurs de la page appliquent leurs modifications :

[!code-cpp[NVC_ATL_Windowing#77](../atl/codesnippet/cpp/example-implementing-a-property-page_5.h)]

L’implémentation de la classe de base de la méthode [Activate](../atl/reference/ipropertypageimpl-class.md#activate) est responsable de la création de la boîte de dialogue et de ses contrôles. Par conséquent, vous pouvez substituer cette méthode et ajouter votre propre initialisation après avoir appelé la classe de base :

[!code-cpp[NVC_ATL_Windowing#78](../atl/codesnippet/cpp/example-implementing-a-property-page_6.h)]

Ce code utilise les méthodes COM de l’interface `Document` pour obtenir les propriétés qui vous intéresse. Il utilise ensuite les wrappers API Win32 fournis par [CDialogImpl](../atl/reference/cdialogimpl-class.md) et ses classes de base pour afficher les valeurs de propriété pour l’utilisateur.

## <a name="overriding-ipropertypageimplapply"></a><a name="vcconoverride_ipropertypageimpl_apply"></a> Substitution de IPropertyPageImpl::Apply

Lorsque les utilisateurs souhaitent appliquer leurs modifications aux objets, le site de la page de propriétés appelle la méthode [Apply](../atl/reference/ipropertypageimpl-class.md#apply). C’est ici que vous devez inverser le code dans `Activate` : alors que `Activate` prenait les valeurs de l’objet pour les transmettre (push) aux contrôles sur la page de propriétés, `Apply` prend les valeurs des contrôles sur la page de propriétés et les transmet (push) à l’objet.

[!code-cpp[NVC_ATL_Windowing#79](../atl/codesnippet/cpp/example-implementing-a-property-page_7.h)]

> [!NOTE]
> La vérification par rapport à [m_bDirty](../atl/reference/ipropertypageimpl-class.md#m_bdirty) au début de cette implémentation est une vérification initiale pour éviter les mises à jour inutiles des objets si `Apply` est appelé plusieurs fois. Il existe également des vérifications par rapport à chacune des valeurs de propriété pour s’assurer que seules les modifications entraînent un appel de méthode vers `Document`.

> [!NOTE]
> `Document` expose `FullName` en tant que propriété en lecture seule. Pour mettre à jour le nom de fichier du document en fonction des modifications apportées à la page de propriétés, vous devez utiliser la méthode `Save` pour enregistrer le fichier avec un nom différent. Par conséquent, le code d’une page de propriétés ne se limite pas à l’obtention ou à la définition de propriétés.

## <a name="displaying-the-property-page"></a><a name="vccontesting_the_property_page"></a> Affichage de la page de propriétés

Pour afficher cette page, vous devez créer un objet d’assistance simple. L’objet d’assistance offrira une méthode qui simplifie l’API `OleCreatePropertyFrame` pour l’affichage d’une page unique connectée à un objet unique. Cette assistance sera conçue de façon à pouvoir être utilisée dans Visual Basic.

Utilisez la [boîte de dialogue Ajouter une classe](../ide/add-class-dialog-box.md) et [l’Assistant Objet simple ATL](../atl/reference/atl-simple-object-wizard.md) pour générer une nouvelle classe, et utilisez `Helper` comme nom court. Une fois la classe créée, ajoutez une méthode comme indiqué dans le tableau ci-dessous.

|Élément|Valeur|
|----------|-----------|
|Nom de la méthode|`ShowPage`|
|Paramètres|`[in] BSTR bstrCaption, [in] BSTR bstrID, [in] IUnknown* pUnk`|

Le paramètre *bstrCaption* correspond à la légende à afficher comme titre pour la boîte de dialogue. Le paramètre *bstrID* est une chaîne représentant un CLSID ou ProgID de la page de propriétés à afficher. Le paramètre *pUnk* est le pointeur `IUnknown` de l’objet dont les propriétés sont configurées par la page de propriétés.

Implémentez la méthode comme indiqué ci-dessous :

[!code-cpp[NVC_ATL_Windowing#80](../atl/codesnippet/cpp/example-implementing-a-property-page_8.cpp)]

## <a name="creating-a-macro"></a><a name="vcconcreating_a_macro"></a> Création d’une macro

Une fois que vous avez créé le projet, vous pouvez tester la page de propriétés et l’objet d’assistance à l’aide d’une macro simple que vous pouvez concevoir et exécuter dans l’environnement de développement Visual Studio. Cette macro va créer un objet d’assistance, puis appeler sa méthode `ShowPage` à l’aide du ProgID de la page de propriétés **DocProperties** et le pointeur `IUnknown` du document actuellement actif dans l’éditeur Visual Studio. Le code dont vous avez besoin pour cette macro est indiqué ci-dessous :

```vb
Imports EnvDTE
Imports System.Diagnostics

Public Module AtlPages

Public Sub Test()
    Dim Helper
    Helper = CreateObject("ATLPages7.Helper.1")

    On Error Resume Next
    Helper.ShowPage( ActiveDocument.Name, "ATLPages7Lib.DocumentProperties.1", DTE.ActiveDocument )
End Sub

End Module
```

Lorsque vous exécutez cette macro, la page de propriétés s’affiche et indique le nom de fichier et l’état en lecture seule du document texte actuellement actif. L’état en lecture seule du document reflète uniquement la capacité à écrire dans le document dans l’environnement de développement ; cela n’affecte pas l’attribut en lecture seule du fichier sur le disque.

::: moniker-end

## <a name="see-also"></a>Voir aussi

[Pages de propriétés](../atl/atl-com-property-pages.md)<br/>
[Exemple ATLPages](../overview/visual-cpp-samples.md)
