---
title: CWordArray, classe
ms.date: 09/07/2019
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
ms.openlocfilehash: c136bbb14e0d7cffc604813731b6f87ba18063cf
ms.sourcegitcommit: 3caf5261b3ea80d9cf14038c116ba981d655cd13
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/11/2019
ms.locfileid: "70907916"
---
# <a name="cwordarray-class"></a>CWordArray, classe

Prend en charge des tableaux de mots de 16 bits.

## <a name="syntax"></a>Syntaxe

```
class CWordArray : public CObject
```

## <a name="members"></a>Membres

Les fonctions membres de `CWordArray` sont similaires aux fonctions membres de la classe [CObArray](../../mfc/reference/cobarray-class.md). Ainsi, vous pouvez utiliser la documentation de référence de `CObArray` pour connaître les spécificités des fonctions membres. Chaque fois que vous voyez un pointeur [CObject](../../mfc/reference/cobject-class.md) comme paramètre de fonction ou valeur de retour, remplacez un mot.

`CObject* CObArray::GetAt( int <nIndex> ) const;`

par exemple, se traduit par

`WORD CWordArray::GetAt( int <nIndex> ) const;`

### <a name="public-constructors"></a>Constructeurs publics

|Nom|Description|
|----------|-----------------|
|[CObArray :: CObArray](../../mfc/reference/cobarray-class.md#cobarray)|Construit un tableau vide.|

### <a name="public-methods"></a>M&#233;thodes publiques

|Nom|Description|
|----------|-----------------|
|[CObArray::Add](../../mfc/reference/cobarray-class.md#add)|Ajoute un élément à la fin du tableau ; étend le tableau si nécessaire.|
|[CObArray :: Append](../../mfc/reference/cobarray-class.md#append)|Ajoute un autre tableau au tableau ; étend le tableau si nécessaire.|
|[CObArray::Copy](../../mfc/reference/cobarray-class.md#copy)|Copie un autre tableau dans le tableau ; étend le tableau si nécessaire.|
|[CObArray :: ElementAt](../../mfc/reference/cobarray-class.md#elementat)|Retourne une référence temporaire au pointeur d'élément dans le tableau.|
|[CObArray :: FreeExtra](../../mfc/reference/cobarray-class.md#freeextra)|Libère toute la mémoire inutilisée au-dessus de la limite supérieure actuelle.|
|[CObArray :: GetAt](../../mfc/reference/cobarray-class.md#getat)|Retourne la valeur à un index donné.|
|[CObArray :: GetCount](../../mfc/reference/cobarray-class.md#getcount)|Obtient le nombre d'éléments dans ce tableau.|
|[CObArray::GetData](../../mfc/reference/cobarray-class.md#getdata)|Autorise l'accès aux éléments du tableau. Peut avoir la valeur NULL.|
|[CObArray::GetSize](../../mfc/reference/cobarray-class.md#getsize)|Obtient le nombre d'éléments dans ce tableau.|
|[CObArray :: GetUpperBound](../../mfc/reference/cobarray-class.md#getupperbound)|Retourne le plus grand index valide.|
|[CObArray :: InsertAt](../../mfc/reference/cobarray-class.md#insertat)|Insère un élément (ou tous les éléments d'un autre tableau) à un index spécifique.|
|[CObArray :: IsEmpty](../../mfc/reference/cobarray-class.md#isempty)|Détermine si le tableau est vide.|
|[CObArray::RemoveAll](../../mfc/reference/cobarray-class.md#removeall)|Supprime tous les éléments de ce tableau.|
|[CObArray::RemoveAt](../../mfc/reference/cobarray-class.md#removeat)|Supprime un élément à un index spécifique.|
|[CObArray :: SetAt](../../mfc/reference/cobarray-class.md#setat)|Définit la valeur d'un index donné. Le tableau n'est pas autorisé à s'étendre.|
|[CObArray::SetAtGrow](../../mfc/reference/cobarray-class.md#setatgrow)|Définit la valeur d'un index donné. Le tableau est étendu si nécessaire.|
|[CObArray::SetSize](../../mfc/reference/cobarray-class.md#setsize)|Définit le nombre d'éléments que ce tableau doit contenir.|

### <a name="public-operators"></a>Op&#233;rateurs publics

|Nom|Description|
|----------|-----------------|
|[CObArray ::, opérateur&#91;&#93;](../../mfc/reference/cobarray-class.md#operator_at)|Définit ou obtient l'élément au niveau de l'index spécifié.|

## <a name="remarks"></a>Notes

`CWordArray`incorpore la macro [IMPLEMENT_SERIAL](run-time-object-model-services.md#implement_serial) pour prendre en charge la sérialisation et le vidage de ses éléments. Si un tableau de mots est stocké dans une archive, soit avec un opérateur d’insertion surchargé, soit avec la fonction membre [CObject :: Serialize](../../mfc/reference/cobject-class.md#serialize) , chaque élément est, à son tour, sérialisé.

> [!NOTE]
>  Avant d'utiliser un tableau, utilisez `SetSize` pour définir sa taille et lui allouer la mémoire nécessaire. Si vous n'utilisez pas `SetSize`, l'ajout d'éléments à votre tableau risque d'entraîner de fréquentes opérations de réallocation et de copie de ce dernier. Les opérations fréquentes de réallocation et de copie sont inefficaces et peuvent fragmenter la mémoire.

Si vous avez besoin d’un vidage d’éléments individuels dans le tableau, vous devez définir la profondeur du contexte de vidage sur une valeur supérieure ou égale à 1.

Pour plus d’informations sur `CWordArray`l’utilisation de, consultez l’article [Collections](../../mfc/collections.md).

## <a name="inheritance-hierarchy"></a>Hiérarchie d'héritage

[CObject](../../mfc/reference/cobject-class.md)

`CWordArray`

## <a name="requirements"></a>Configuration requise

**En-tête :** afxcoll. h

##  <a name="icommandsource_interface"></a>Interface ICommandSource

Gère les commandes envoyées à partir d’un objet source de commande à un contrôle utilisateur.

```
interface class ICommandSource
```

### <a name="remarks"></a>Notes

Quand vous hébergez un contrôle utilisateur dans une vue MFC, la [classe CWinFormsView](../../mfc/reference/cwinformsview-class.md) achemine les commandes et met à jour les messages de l’interface utilisateur de commande au contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu Frame et les boutons de barre d’outils). En implémentant, vous donnez à l’utilisateur le contrôle d' `ICommandSource` une référence à l’objet.

Voir [Guide pratique pour Ajoutez le routage des commandes au contrôle](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Windows Forms pour obtenir un exemple d’utilisation `ICommandTarget`de.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="addcommandhandler"></a>  ICommandSource::AddCommandHandler

Ajoute un gestionnaire de commandes à un objet source de commande.

```
void AddCommandHandler(
    unsigned int cmdID,
    CommandHandler^ cmdHandler);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

*cmdHandler*<br/>
Handle de la méthode du gestionnaire de commandes.

### <a name="remarks"></a>Notes

Cette méthode ajoute le gestionnaire de commandes *cmdHandler* à l’objet source de la commande et mappe le gestionnaire à *cmdID*.

Voir [Guide pratique pour Ajoutez le routage des commandes au contrôle](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Windows Forms pour obtenir un exemple d’utilisation `AddCommandHandler`de.

##  <a name="addcommandrangehandler"></a>  ICommandSource::AddCommandRangeHandler

Ajoute un groupe de gestionnaires de commandes à un objet source de commande.

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
Handle de la méthode de gestionnaire de messages à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes

Cette méthode mappe une plage contiguë d’ID de commandes à un seul gestionnaire de messages et l’ajoute à l’objet source de la commande. Cela permet de gérer un groupe de boutons associés avec une méthode.

##  <a name="addcommandrangeuihandler"></a>  ICommandSource::AddCommandRangeUIHandler

Ajoute un groupe de gestionnaires de messages de commande d’interface utilisateur à un objet source de commande.

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
Handle de la méthode de gestionnaire de messages à laquelle les commandes sont mappées.

### <a name="remarks"></a>Notes

Cette méthode mappe une plage contiguë d’ID de commandes à un gestionnaire de messages de commande d’interface utilisateur unique et l’ajoute à l’objet source de la commande. Cela permet de gérer un groupe de boutons associés avec une méthode.

##  <a name="addcommanduihandler"></a>  ICommandSource::AddCommandUIHandler

Ajoute un gestionnaire de messages de commande d’interface utilisateur à un objet source de commande.

```
void AddCommandUIHandler(
    unsigned int cmdID,
    CommandUIHandler^ cmdUIHandler);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

*cmdUIHandler*<br/>
Handle de la méthode du gestionnaire de messages de commande de l’interface utilisateur.

### <a name="remarks"></a>Notes

Cette méthode ajoute le gestionnaire de messages de commande de l’interface utilisateur *cmdHandler* à l’objet source de la commande et mappe le gestionnaire à *cmdID*.

##  <a name="postcommand"></a>  ICommandSource::PostCommand

Publie un message sans attendre qu’il soit traité.

```
void PostCommand(unsigned int command);
```

### <a name="parameters"></a>Paramètres

*command*<br/>
ID de commande du message à publier.

### <a name="remarks"></a>Notes

Cette méthode publie de manière asynchrone le message mappé à l’ID spécifié par la *commande*. Il appelle [CWnd ::P ostmessage](../../mfc/reference/cwnd-class.md#postmessage) pour placer le message dans la file d’attente de messages de la fenêtre, puis retourne sans attendre que la fenêtre correspondante traite le message.

##  <a name="removecommandhandler"></a>  ICommandSource::RemoveCommandHandler

Supprime un gestionnaire de commandes d’un objet source de commande.

```
void RemoveCommandHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

### <a name="remarks"></a>Notes

Cette méthode supprime le gestionnaire de commandes mappé à *cmdID* de l’objet source de la commande.

##  <a name="removecommandrangehandler"></a>  ICommandSource::RemoveCommandRangeHandler

Supprime un groupe de gestionnaires de commandes d’un objet source de commande.

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

Cette méthode supprime un groupe de gestionnaires de messages, mappé aux ID de commande spécifiés par *cmdIDMin* et *cmdIDMax*, à partir de l’objet source de la commande.

##  <a name="removecommandrangeuihandler"></a>  ICommandSource::RemoveCommandRangeUIHandler

Supprime un groupe de gestionnaires de messages de commande d’interface utilisateur d’un objet source de commande.

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

Cette méthode supprime un groupe de gestionnaires de messages de commande d’interface utilisateur, mappés aux ID de commande spécifiés par *cmdIDMin* et *cmdIDMax*, à partir de l’objet source de la commande.

##  <a name="removecommanduihandler"></a>  ICommandSource::RemoveCommandUIHandler

Supprime un gestionnaire de messages de commande de l’interface utilisateur d’un objet source de commande.

```
void RemoveCommandUIHandler(unsigned int cmdID);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

### <a name="remarks"></a>Notes

Cette méthode supprime le gestionnaire de messages de commande de l’interface utilisateur mappé à *cmdID* à partir de l’objet source de la commande.

##  <a name="sendcommand"></a>  ICommandSource::SendCommand

Envoie un message et attend qu’il soit traité avant de retourner.

```
void SendCommand(unsigned int command);
```

### <a name="parameters"></a>Paramètres

*command*<br/>
ID de commande du message à envoyer.

### <a name="remarks"></a>Notes

Cette méthode envoie de façon synchrone le message mappé à l’ID spécifié par la *commande*. Il appelle [CWnd :: SendMessage](../../mfc/reference/cwnd-class.md#sendmessage) pour placer le message dans la file d’attente de messages de la fenêtre et attend que cette procédure de fenêtre ait traité le message avant de retourner.

##  <a name="icommandtarget_interface"></a>  ICommandTarget Interface

Fournit un contrôle utilisateur avec une interface pour recevoir des commandes d’un objet source de commande.

```
interface class ICommandTarget
```

### <a name="remarks"></a>Notes

Quand vous hébergez un contrôle utilisateur dans une vue MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) achemine les commandes et met à jour les messages de l’interface utilisateur vers le contrôle utilisateur pour lui permettre de gérer les commandes MFC (par exemple, les éléments de menu Frame et les boutons de barre d’outils). En implémentant `ICommandTarget`, vous donnez à l’utilisateur le contrôle d’une référence à l’objet.

Voir [Guide pratique pour Ajoutez le routage des commandes au contrôle](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Windows Forms pour obtenir un exemple d’utilisation `ICommandTarget`de.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="initialize"></a>  ICommandTarget::Initialize

Initialise l’objet de la cible de la commande.

```
void Initialize(ICommandSource^ cmdSource);
```

### <a name="parameters"></a>Paramètres

*cmdSource*<br/>
Handle de l’objet source de la commande.

### <a name="remarks"></a>Notes

Quand vous hébergez un contrôle utilisateur dans une vue MFC, [CWinFormsView](../../mfc/reference/cwinformsview-class.md) achemine les commandes et met à jour les messages de l’interface utilisateur vers le contrôle utilisateur pour lui permettre de gérer les commandes MFC.

Cette méthode initialise l’objet de la cible de commande et l’associe à l’objet de source de commande spécifié *cmdSource*. Elle doit être appelée dans l’implémentation de la classe de contrôle utilisateur. Lors de l’initialisation, vous devez inscrire les gestionnaires de commandes avec l’objet source de commande en appelant [ICommandSource :: AddCommandHandler](../../mfc/reference/icommandsource-interface.md) dans l' `Initialize` implémentation. Voir [Guide pratique pour Ajoutez le routage des commandes au contrôle](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md) Windows Forms pour obtenir un exemple d’utilisation `Initialize` de.

##  <a name="icommandui_interface"></a>Interface ICommandUI

Gère les commandes de l’interface utilisateur.

```
interface class ICommandUI
```

### <a name="remarks"></a>Notes

Cette interface fournit des méthodes et des propriétés qui gèrent les commandes de l’interface utilisateur. `ICommandUI`est similaire à la [classe CCmdUI](../../mfc/reference/ccmdui-class.md), sauf `ICommandUI` que est utilisé pour les applications MFC qui interagissent avec les composants .net.

`ICommandUI`est utilisé dans un `ON_UPDATE_COMMAND_UI` gestionnaire d’une classe dérivée de. Lorsqu’un utilisateur d’une application active (sélectionne ou clique) un menu, chaque élément de menu est affiché comme activé ou désactivé. La cible de chaque commande de menu fournit ces informations en implémentant un `ON_UPDATE_COMMAND_UI` gestionnaire. Pour chacun des objets de l’interface utilisateur de commande de votre application, utilisez l' [Assistant classe](mfc-class-wizard.md) ou la fenêtre **propriétés** (dans **affichage de classes**) pour créer une entrée de table des messages et un prototype de fonction pour chaque gestionnaire.

Pour plus d’informations sur l' `ICommandUI` utilisation de l’interface dans le routage des [commandes, consultez Procédure : Ajoutez le routage des commandes au contrôle](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)Windows Forms.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

Pour plus d’informations sur la façon dont les commandes de l’interface utilisateur sont gérées dans MFC, consultez la [classe CCmdUI](../../mfc/reference/ccmdui-class.md).

##  <a name="check"></a>  ICommandUI::Check

Affecte l’état d’activation approprié à l’élément d’interface utilisateur pour cette commande.

```
property UICheckState Check;
```

### <a name="remarks"></a>Notes

Cette propriété affecte l’état d’activation approprié à l’élément d’interface utilisateur pour cette commande. Définissez `Check` les valeurs suivantes :

|Terme|Définition|
|----------|----------------|
|0|Décochez|
|1|Valider|
|2|Définir comme indéterminé|

##  <a name="continuerouting"></a>  ICommandUI::ContinueRouting

Indique au mécanisme de routage des commandes de continuer à acheminer le message actuel vers le dessous de la chaîne de gestionnaires.

```
void ContinueRouting();
```

### <a name="remarks"></a>Notes

Il s’agit d’une fonction membre avancée qui doit être utilisée conjointement avec un gestionnaire [ON_COMMAND_EX](message-map-macros-mfc.md#on_command_ex) qui retourne false. Pour plus d’informations, consultez Technical [note TN006 : Tables](../../mfc/tn006-message-maps.md)des messages.

##  <a name="enabled"></a>  ICommandUI::Enabled

Active ou désactive l’élément d’interface utilisateur pour cette commande.

```
property bool Enabled;
```

### <a name="remarks"></a>Notes

Cette propriété active ou désactive l’élément d’interface utilisateur pour cette commande. Affectez `Enabled` la valeur true pour activer l’élément, false pour le désactiver.

##  <a name="id"></a>  ICommandUI::ID

Obtient l’ID de l’objet d’interface utilisateur représenté par `ICommandUI` l’objet.

```
property unsigned int ID;
```

### <a name="remarks"></a>Notes

Cette propriété obtient l’ID (un handle) de l’élément de menu, du bouton de barre d’outils ou d’un autre `ICommandUI` objet d’interface utilisateur représenté par l’objet.

##  <a name="index"></a>  ICommandUI::Index

Obtient l’index de l’objet d’interface utilisateur représenté par `ICommandUI` l’objet.

```
property unsigned int Index;
```

### <a name="remarks"></a>Notes

Cette propriété obtient l’index (un handle) de l’élément de menu, du bouton de barre d’outils ou d’un autre `ICommandUI` objet d’interface utilisateur représenté par l’objet.

##  <a name="radio"></a>  ICommandUI::Radio

Affecte l’état d’activation approprié à l’élément d’interface utilisateur pour cette commande.

```
property bool Radio;
```

### <a name="remarks"></a>Notes

Cette propriété affecte l’état d’activation approprié à l’élément d’interface utilisateur pour cette commande. Affectez `Radio` la valeur true pour activer l’élément ; sinon, false.

##  <a name="text"></a>  ICommandUI::Text

Définit le texte de l’élément d’interface utilisateur pour cette commande.

```
property String^ Text;
```

### <a name="remarks"></a>Notes

Cette propriété définit le texte de l’élément d’interface utilisateur pour cette commande. Définissez `Text` sur un handle de chaîne de texte.

##  <a name="iview_interface"></a>Interface IView

Implémente plusieurs méthodes que [CWinFormsView](../../mfc/reference/cwinformsview-class.md) utilise pour envoyer des notifications d’affichage à un contrôle managé.

```
interface class IView
```

### <a name="remarks"></a>Notes

`IView`implémente plusieurs méthodes qui `CWinFormsView` utilisent pour transférer les notifications d’affichage courantes à un contrôle managé hébergé. Il s’agit des [OnInitialUpdate](../../mfc/reference/iview-interface.md), [OnUpdate](../../mfc/reference/iview-interface.md) et [OnActivateView](../../mfc/reference/iview-interface.md).

`IView`est semblable à [CView](../../mfc/reference/cview-class.md), mais est utilisé uniquement avec les vues et les contrôles managés.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

##  <a name="onactivateview"></a>  IView::OnActivateView

Appelée par MFC lorsqu’une vue est activée ou désactivée.

```
void OnActivateView(bool activate);
```

### <a name="parameters"></a>Paramètres

*activate*<br/>
Indique si la vue est en cours d’activation ou de désactivation.

##  <a name="oninitialupdate"></a>  IView::OnInitialUpdate

Appelée par l’infrastructure après que la vue a été attachée pour la première fois au document, mais avant l’affichage initial de la vue.

```
void OnInitialUpdate();
```

##  <a name="onupdate"></a>  IView::OnUpdate

Appelée par MFC après la modification du document de la vue.

```
void OnUpdate();
```

### <a name="remarks"></a>Notes

Cette fonction permet à la vue de mettre à jour son affichage pour refléter les modifications.

## <a name="see-also"></a>Voir aussi

[Exemple de collecte MFC](../../overview/visual-cpp-samples.md)<br/>
[CObject, classe](../../mfc/reference/cobject-class.md)<br/>
[Graphique hiérarchique](../../mfc/hierarchy-chart.md)
