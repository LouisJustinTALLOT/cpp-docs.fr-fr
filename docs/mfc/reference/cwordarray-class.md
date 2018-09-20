---
title: CWordArray, classe | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- CWordArray
- AFXCOLL/CWordArray
- AFXCOLL/CObArray::CObArray
- AFXCOLL/CObArray::Add
- AFXCOLL/CObArray::Append
- AFXCOLL/CObArray::Copy
- AFXCOLL/CObArray::ElementAt
- AFXCOLL/CObArray::FreeExtra
- AFXCOLL/CObArray::GetAt
- AFXCOLL/CObArray::GetCount
- AFXCOLL/CObArray::GetData
- AFXCOLL/CObArray::GetSize
- AFXCOLL/CObArray::GetUpperBound
- AFXCOLL/CObArray::InsertAt
- AFXCOLL/CObArray::IsEmpty
- AFXCOLL/CObArray::RemoveAll
- AFXCOLL/CObArray::RemoveAt
- AFXCOLL/CObArray::SetAt
- AFXCOLL/CObArray::SetAtGrow
- AFXCOLL/CObArray::SetSize
dev_langs:
- C++
helpviewer_keywords:
- CObArray [MFC], CObArray
- CObArray [MFC], Add
- CObArray [MFC], Append
- CObArray [MFC], Copy
- CObArray [MFC], ElementAt
- CObArray [MFC], FreeExtra
- CObArray [MFC], GetAt
- CObArray [MFC], GetCount
- CObArray [MFC], GetData
- CObArray [MFC], GetSize
- CObArray [MFC], GetUpperBound
- CObArray [MFC], InsertAt
- CObArray [MFC], IsEmpty
- CObArray [MFC], RemoveAll
- CObArray [MFC], RemoveAt
- CObArray [MFC], SetAt
- CObArray [MFC], SetAtGrow
- CObArray [MFC], SetSize
ms.assetid: 2ba2c194-2c6c-40ff-9db4-e9dbe57e1f57
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: cddcf337c68908d58749623e0739f3cb5979fa91
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46387950"
---
# <a name="cwordarray-class"></a>CWordArray, classe

Prend en charge des tableaux de mots de 16 bits.

## <a name="syntax"></a>Syntaxe

```
class CWordArray : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CWordArray` sont similaires aux fonctions membres de classe [CObArray](../../mfc/reference/cobarray-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObArray` pour connaître les spécificités des fonctions membres. Partout où vous voyez un [CObject](../../mfc/reference/cobject-class.md) pointeur en tant que paramètre de fonction ou valeur de retour, remplacer un mot.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

par exemple, se traduit par

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CObArray::CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Construit un tableau vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|
|[CObArray::Append](../../mfc/reference/cobarray-class.md#append)|Ajoute un autre tableau au tableau ; étend le tableau si nécessaire.|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CObArray::ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CObArray::FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|
|[CObArray::GetAt](../../mfc/reference/cobarray-class.md#getat)|Retourne la valeur à un index donné.|
|[CObArray::GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtient le nombre d'éléments dans ce tableau.|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Autorise l'accès aux éléments du tableau. Peut être NULL.|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Obtient le nombre d'éléments dans ce tableau.|
|[CObArray::GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Retourne le plus grand index valide.|
|[CObArray::InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CObArray::IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Détermine si le tableau est vide.|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Supprime tous les éléments de ce tableau.|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Supprime un élément à un index spécifique.|
|[CObArray::SetAt](../../mfc/reference/cobarray-class.md#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Définit le nombre d'éléments que ce tableau doit contenir.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CObArray::operator&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

`CWordArray` incorpore le [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) macro pour prendre en charge la sérialisation et le vidage de ses éléments. Si un tableau de mots est stocké dans une archive, avec un opérateur d’insertion surchargé ou avec le [CObject::Serialize](../../mfc/reference/cobject-class.md#serialize) fonction membre, chaque élément est, à son tour, sérialisé.

> [!NOTE]
>  Avant d'utiliser un tableau, utilisez `SetSize` pour définir sa taille et lui allouer la mémoire nécessaire. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Si vous avez besoin de vider des éléments individuels dans le tableau, vous devez définir la profondeur du contexte de vidage à 1 ou supérieur.

Pour plus d’informations sur l’utilisation de `CWordArray`, consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcoll.h

##  <a name="icommandsource_interface"></a>  ICommandSource, Interface

Gère les commandes envoyées à partir d’un objet de source de commande à un contrôle utilisateur.

```
interface class ICommandSource
```

### <a name="remarks"></a>Notes

Lorsque vous hébergez un contrôle utilisateur dans une vue de MFC, [CWinFormsView, classe](../../mfc/reference/cwinformsview-class.md) commandes d’itinéraires et mise à jour de commande des messages de l’interface utilisateur pour le contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu de frame et boutons de barre d’outils). En mettant en œuvre, vous donner le contrôle utilisateur une référence à la `ICommandSource` objet.

Consultez [Comment : ajouter routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple montrant comment utiliser `ICommandTarget`.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

Ajoute un gestionnaire de commandes à un objet de source de commande.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

*cmdHandler*<br/>
Handle vers la méthode de gestionnaire de commande.

### <a name="remarks"></a>Notes

Cette méthode ajoute le Gestionnaire de commandes *cmdHandler* à l’objet de source de commande et mappe le gestionnaire à *cmdID*.

Consultez [Comment : ajouter routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple montrant comment utiliser `AddCommandHandler`.

##  <a name="addcommandrangehandler"></a>  ICommandSource::AddCommandRangeHandler

Ajoute un groupe de gestionnaires de commandes à un objet de source de commande.

```
void AddCommandRangeHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
Index de début de la plage d’ID de commande.

*cmdIDMax*<br/>
Index de fin de la plage d’ID de commande.

*cmdHandler*<br/>
Handle vers la méthode de gestionnaire de message à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes

Cette méthode mappe une plage contiguë d’ID de commande à un seul gestionnaire de messages et l’ajoute à l’objet de source de commande. Cela est utilisé pour gérer un groupe de boutons associés avec une méthode.

##  <a name="addcommandrangeuihandler"></a>  ICommandSource::AddCommandRangeUIHandler

Ajoute un groupe de gestionnaires de messages de commande interface utilisateur à un objet de source de commande.

```
void AddCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
Index de début de la plage d’ID de commande.

*cmdIDMax*<br/>
Index de fin de la plage d’ID de commande.

*cmdHandler*<br/>
Handle vers la méthode de gestionnaire de message à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes

Cette méthode mappe une plage contiguë d’ID de commande à un gestionnaire de messages de commande interface utilisateur unique et l’ajoute à l’objet de source de commande. Cela est utilisé pour gérer un groupe de boutons associés avec une méthode.

##  <a name="addcommanduihandler"></a>  ICommandSource::AddCommandUIHandler

Ajoute un gestionnaire de messages de commande interface utilisateur à un objet de source de commande.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

*cmdUIHandler*<br/>
Handle vers la méthode de gestionnaire de message de commande utilisateur interface.

### <a name="remarks"></a>Notes

Cette méthode ajoute le Gestionnaire de messages de commande interface utilisateur *cmdHandler* à l’objet de source de commande et mappe le gestionnaire à *cmdID*.

##  <a name="postcommand"></a>  ICommandSource::PostCommand

Publie un message sans attendre qu’il soit traité.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Paramètres

*command*<br/>
L’ID de commande du message à publier.

### <a name="remarks"></a>Notes

Cette méthode publie façon asynchrone le message mappé à l’ID spécifié par *commande*. Il appelle [CWnd::PostMessage](../../mfc/reference/cwnd-class.md#postmessage) pour placer le message dans la fenêtre file d’attente de message, puis renvoie sans attendre que la fenêtre correspondante traiter le message.

##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler

Supprime un gestionnaire de commandes à partir d’un objet de source de commande.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

### <a name="remarks"></a>Notes

Cette méthode supprime le Gestionnaire de commandes mappé à *cmdID* à partir de l’objet de source de commande.

##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler

Supprime un groupe de gestionnaires de commandes à partir d’un objet de source de commande.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
Index de début de la plage d’ID de commande.

*cmdIDMax*<br/>
Index de fin de la plage d’ID de commande.

### <a name="remarks"></a>Notes

Cette méthode supprime un groupe de gestionnaires de messages, mappé la spécifiée d’ID de commande par *cmdIDMin* et *cmdIDMax*, à partir de l’objet de source de commande.

##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler

Supprime un groupe de gestionnaires de messages de commande interface utilisateur à partir d’un objet de source de commande.

```
void RemoveCommandRangeUIHandler(
    unsigned int cmdIDMin,
    unsigned int cmdIDMax);
```

### <a name="parameters"></a>Paramètres

*cmdIDMin*<br/>
Index de début de la plage d’ID de commande.

*cmdIDMax*<br/>
Index de fin de la plage d’ID de commande.

### <a name="remarks"></a>Notes

Cette méthode supprime un groupe de gestionnaires de messages de commande interface utilisateur, mappé la spécifiée d’ID de commande par *cmdIDMin* et *cmdIDMax*, à partir de l’objet de source de commande.

##  <a name="removecommanduihandler"></a>  ICommandSource::RemoveCommandUIHandler

Supprime un gestionnaire de messages de commande interface utilisateur à partir d’un objet de source de commande.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

### <a name="remarks"></a>Notes

Cette méthode supprime le Gestionnaire de messages de commande d’interface utilisateur mappé à *cmdID* à partir de l’objet de source de commande.

##  <a name="sendcommand"></a>  ICommandSource::SendCommand

Envoie un message et attend qu’il soit traité avant de retourner.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Paramètres

*command*<br/>
L’ID de commande du message à envoyer.

### <a name="remarks"></a>Notes

Cette méthode envoie de façon synchrone le message mappé à l’ID spécifié par *commande*. Il appelle [CWnd::SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) pour placer le message dans la fenêtre file d’attente de message et attend jusqu'à ce que cette procédure de fenêtre ait traité le message avant de retourner.

##  <a name="icommandtarget_interface"></a>  ICommandTarget, Interface

Fournit un contrôle utilisateur avec une interface pour recevoir des commandes à partir d’un objet de source de commande.

```
interface class ICommandTarget
```

### <a name="remarks"></a>Notes

Lorsque vous hébergez un contrôle utilisateur dans une vue de MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) commandes d’itinéraires et mise à jour de commande des messages de l’interface utilisateur pour le contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu de frame et boutons de barre d’outils). En implémentant `ICommandTarget`, vous donner le contrôle utilisateur, une référence à l’objet.

Consultez [Comment : ajouter routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple montrant comment utiliser `ICommandTarget`.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="initialize"></a>  ICommandTarget::Initialize

Initialise l’objet cible de commande.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Paramètres

*cmdSource*<br/>
Handle vers l’objet de source de commande.

### <a name="remarks"></a>Notes

Lorsque vous hébergez un contrôle utilisateur dans une vue de MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) commandes d’itinéraires et mise à jour des messages de l’interface utilisateur pour le contrôle utilisateur pour lui permettre de gérer les commandes MFC de commande.

Cette méthode initialise l’objet cible de commande et l’associe à l’objet de source de commande spécifiée *cmdSource*. Il doit être appelée dans l’implémentation de classe de contrôle utilisateur. Lors de l’initialisation, vous devez inscrire des gestionnaires de commandes avec l’objet de source de commande en appelant [ICommandSource::AddCommandHandler](../../mfc/reference/icommandsource-interface.md) dans le `Initialize` implémentation. Consultez [Comment : ajouter routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) pour obtenir un exemple montrant comment utiliser `Initialize` pour ce faire.

##  <a name="icommandui_interface"></a>  Icommandui, Interface

Gère les commandes de l’interface utilisateur.

```
interface class ICommandUI
```

### <a name="remarks"></a>Notes

Cette interface fournit des méthodes et propriétés qui gèrent des commandes de l’interface utilisateur. `ICommandUI` est similaire à [CCmdUI, classe](../../mfc/reference/ccmdui-class.md), sauf que `ICommandUI` est utilisé pour les applications MFC qui interagissent avec des composants .NET.

`ICommandUI` est utilisé dans un `ON_UPDATE_COMMAND_UI` gestionnaire dans-classe dérivée. Lorsqu’un utilisateur d’une application active (sélectionne ou clics) un menu, chaque élément de menu est affiché comme activé ou désactivé. La cible de chaque commande de menu fournit ces informations en implémentant un `ON_UPDATE_COMMAND_UI` gestionnaire. Pour chacun des objets d’interface utilisateur commande dans votre application, utilisez la fenêtre Propriétés pour créer une entrée de table des messages et le prototype de fonction pour chaque gestionnaire.

Pour plus d’informations sur la façon dont le `ICommandUI` interface est utilisée dans le routage des commandes, consultez [Comment : ajouter routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Pour plus d’informations sur la gestion des commandes de l’interface utilisateur dans MFC, consultez [CCmdUI, classe](../../mfc/reference/ccmdui-class.md).

##  <a name="check"></a>  ICommandUI::Check

Définit l’élément d’interface utilisateur pour cette commande à l’état de vérification appropriée.

```
property UICheckState Check;
```

### <a name="remarks"></a>Notes

Cette propriété définit l’élément d’interface utilisateur pour cette commande à l’état de vérification appropriée. Définissez `Check` les valeurs suivantes :

|Terme|Définition|
|----------|----------------|
|0|Décochez la case|
|1|Valider|
|2|Ensemble indéterminé|

##  <a name="continuerouting"></a>  ICommandUI::ContinueRouting

Indique au mécanisme de routage de commande pour continuer le message en cours dans la chaîne de gestionnaires de routage.

```
void ContinueRouting();
```

### <a name="remarks"></a>Notes

Il s’agit d’une fonction membre avancé qui doit être utilisée conjointement avec un [ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex) gestionnaire qui retourne la valeur FALSE. Pour plus d’informations, consultez la Note technique [TN006 : tables des messages](../../mfc/tn006-message-maps.md).

##  <a name="enabled"></a>  ICommandUI::Enabled

Active ou désactive l’élément d’interface utilisateur pour cette commande.

```
property bool Enabled;
```

### <a name="remarks"></a>Notes

Cette propriété Active ou désactive l’élément d’interface utilisateur pour cette commande. Définissez `Enabled` sur TRUE pour activer l’élément, FALSE pour le désactiver.

##  <a name="id"></a>  ICommandUI::ID

Obtient l’ID de l’objet d’interface utilisateur représenté par le `ICommandUI` objet.

```
property unsigned int ID;
```

### <a name="remarks"></a>Notes

Cette propriété obtient l’ID (un handle) de l’élément de menu, le bouton de barre d’outils, ou autre objet d’interface utilisateur représenté par le `ICommandUI` objet.

##  <a name="index"></a>  ICommandUI::Index

Obtient l’index de l’objet d’interface utilisateur représenté par le `ICommandUI` objet.

```
property unsigned int Index;
```

### <a name="remarks"></a>Notes

Cette propriété obtient l’index (un handle) de l’élément de menu, le bouton de barre d’outils, ou autre objet d’interface utilisateur représenté par le `ICommandUI` objet.

##  <a name="radio"></a>  ICommandUI::Radio

Définit l’élément d’interface utilisateur pour cette commande à l’état de vérification appropriée.

```
property bool Radio;
```

### <a name="remarks"></a>Notes

Cette propriété définit l’élément d’interface utilisateur pour cette commande à l’état de vérification appropriée. Définissez `Radio` sur TRUE pour activer l’élément ; sinon, FALSE.

##  <a name="text"></a>  ICommandUI::Text

Définit le texte de l’élément d’interface utilisateur pour cette commande.

```
property String^ Text;
```

### <a name="remarks"></a>Notes

Cette propriété définit le texte de l’élément d’interface utilisateur pour cette commande. Définissez `Text` à un handle de chaîne de texte.

##  <a name="iview_interface"></a>  Interface IView

Implémente plusieurs méthodes qui [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utilise pour envoyer des notifications d’affichage à un contrôle géré.

```
interface class IView
```

### <a name="remarks"></a>Notes

`IView` implémente plusieurs méthodes qui `CWinFormsView` utilise pour transférer les notifications d’affichage communes à un contrôle géré hébergé. Il s’agit de [OnInitialUpdate](../../mfc/reference/iview-interface.md), [OnUpdate](../../mfc/reference/iview-interface.md) et [OnActivateView](../../mfc/reference/iview-interface.md).

`IView` est similaire à [CView](../../mfc/reference/cview-class.md), mais est utilisé uniquement avec des vues gérées et des contrôles.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="onactivateview"></a>  IView::OnActivateView

Appelé par MFC lorsqu’une vue est activée ou désactivée.

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>Paramètres

*Activer*<br/>
Indique si la vue est activée ou désactivée.

##  <a name="oninitialupdate"></a>  IView::OnInitialUpdate

Appelé par l’infrastructure une fois que la vue est d’abord attachée au document, mais avant l’affichage initial.

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>  IView::OnUpdate

Appelé par MFC, une fois que le document de la vue a été modifié.

```
void OnUpdate();
```

### <a name="remarks"></a>Notes

Cette fonction permet l’affichage pour mettre à jour son affichage afin de refléter les modifications.

## <a name="see-also"></a>Voir aussi

[Exemple MFC COLLECT](../../visual-cpp-samples.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)



