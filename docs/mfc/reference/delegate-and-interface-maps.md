---
title: Délégué et Macros de mappage d’Interface (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: cd1f38236baf2caca9f2a2a426f28f797291fb13
ms.sourcegitcommit: afd6fac7c519dbc47a4befaece14a919d4e0a8a2
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 11/10/2018
ms.locfileid: "51524649"
---
# <a name="delegate-and-interface-map-macros"></a>Macros de mappage d’interface et délégué

MFC prend en charge ces macros pour les cartes d’interface et délégué :

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Commence un mappage de délégué.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Commence la définition de la carte interfaced.|
|[CommandHandler (délégué)](#commandhandler)|Inscrit les méthodes de rappel avec une source de commande.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Met fin à une carte de délégué.|
|[END_INTERFACE_MAP](#end_interface_map)|Met fin à la carte d’interface dans le fichier d’implémentation. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Crée une entrée dans le mappage de délégué.|
|[INTERFACE_PART](#interface_part)|Utilisé entre le BEGIN_INTERFACE_MAP (macro) et la macro END_INTERFACE_MAP pour chaque interface que votre objet prendra en charge.|
|[MAKE_DELEGATE](#make_delegate)|Attache un gestionnaire d’événements à un contrôle géré.|

## <a name="begin_delegate_map"></a> BEGIN_DELEGATE_MAP

Commence un mappage de délégué.

### <a name="syntax"></a>Syntaxe

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Paramètres

*CLASSE*<br/>
La classe dans lequel est hébergé le contrôle managé.

### <a name="remarks"></a>Notes

Cette macro marque le début d’une liste d’entrées de délégué, qui se compose d’un mappage de délégué. Pour obtenir un exemple d’utilisation de cette macro, consultez [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Configuration requise

**En-tête :** msclr\event.h

### <a name="see-also"></a>Voir aussi

[Guide pratique pour recevoir des événements Windows Forms de classes C++ natives](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Commence la définition de la carte interfaced lorsqu’il est utilisé dans le fichier d’implémentation.

### <a name="syntax"></a>Syntaxe

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Classe dans laquelle la table d'interface doit être définie.

*classe de base*<br/>
La classe à partir de laquelle *theClass* dérive.

### <a name="remarks"></a>Notes

Pour chaque interface est implémentée, il existe un ou plusieurs appels de macro INTERFACE_PART. Pour chaque agrégat qui utilise la classe, il existe un appel de macro INTERFACE_AGGREGATE.

Pour plus d’informations sur les cartes d’interface, consultez [Technical Note 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="commandhandler"></a>CommandHandler (délégué)

Inscrit les méthodes de rappel avec une source de commande.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

### <a name="remarks"></a>Notes

Ce délégué inscrit les méthodes de rappel avec une source de commande. Lorsque vous ajoutez un délégué à l’objet de source de commande, la méthode de rappel devient un gestionnaire de commandes provenant de la source spécifiée.

Pour plus d’informations, consultez [Comment : ajouter routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

### <a name="see-also"></a>Voir aussi

[Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)

##  <a name="commanduihandler"></a>CommandUIHandler

Inscrit les méthodes de rappel avec un message de commande de mise à jour interface utilisateur.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

*cmdUI*<br/>
ID de message de commande.

### <a name="remarks"></a>Notes

Ce délégué inscrit les méthodes de rappel avec un message de commande de mise à jour interface utilisateur. `CommandUIHandler` est similaire à [CommandHandler](#commandhandler) , à ceci près que ce délégué est utilisé avec les commandes de mise à jour l’objet interface utilisateur. Commandes de mise à jour l’interface utilisateur doivent être mappés un à un avec les méthodes de gestionnaire de message.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [à l’aide d’un contrôle d’utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwinforms.h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

### <a name="see-also"></a>Voir aussi

[Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[CommandHandler](#commandhandler)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

Met fin à une carte de délégué.

### <a name="syntax"></a>Syntaxe

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Notes

Cette macro marque la fin d’une liste d’entrées de délégué, qui se compose d’un mappage de délégué. Pour obtenir un exemple d’utilisation de cette macro, consultez [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Configuration requise

**En-tête :** msclr\event.h

### <a name="see-also"></a>Voir aussi

[Guide pratique pour recevoir des événements Windows Forms de classes C++ natives](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

Met fin à la carte d’interface dans le fichier d’implémentation.

### <a name="syntax"></a>Syntaxe

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les cartes d’interface, consultez [Technical Note 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

### <a name="see-also"></a>Voir aussi

[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
[BEGIN_INTERFACE_MAP](#begin_interface_map)

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Crée une entrée dans le mappage de délégué.

### <a name="syntax"></a>Syntaxe

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Paramètres

*MEMBRE*<br/>
La méthode de gestionnaire d’événements à attacher au contrôle.

*ARG0*<br/>
Le premier argument de la méthode de gestionnaire d’événement managé, tel que `Object^`.

*ARG1*<br/>
Le deuxième argument de la méthode de gestionnaire d’événement managé, tel que `EventArgs^`.

### <a name="remarks"></a>Notes

Chaque entrée dans le mappage de délégué correspond à un délégué de gestionnaire d’événements managés créé par [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Exemple

L’exemple de code suivant montre comment utiliser EVENT_DELEGATE_ENTRY pour créer une entrée dans le mappage de délégué pour le `OnClick` Gestionnaire d’événements ; également voir l’exemple de code dans MAKE_DELEGATE. Pour plus d’informations, consultez [Comment : récepteur d’événements Windows Forms à partir de Classes C++ natives](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Configuration requise

**En-tête :** msclr\event.h

### <a name="see-also"></a>Voir aussi

[MAKE_DELEGATE](#make_delegate)<br/>
[BEGIN_DELEGATE_MAP](#begin_delegate_map)<br/>
[END_DELEGATE_MAP](#end_delegate_map)

##  <a name="interface_part"></a>INTERFACE_PART

Utilisé entre le BEGIN_INTERFACE_MAP (macro) et la macro END_INTERFACE_MAP pour chaque interface que votre objet prendra en charge.

### <a name="syntax"></a>Syntaxe

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Paramètres

*theClass*<br/>
Nom de la classe qui contient la table d'interface.
*IID*<br/>
IID qui doit être mappée à la classe incorporée.
*localClass*<br/>
Le nom de la classe locale.

### <a name="remarks"></a>Notes

Il vous permet de mapper un IID à un membre de la classe indiquée par *theClass* et *localClass*.

Pour plus d’informations sur les cartes d’interface, consultez [Technical Note 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxwin.h

##  <a name="make_delegate"></a>MAKE_DELEGATE

Attache un gestionnaire d’événements à un contrôle géré.

### <a name="syntax"></a>Syntaxe

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Paramètres

*DÉLÉGUÉ*<br/>
Déléguer le type du Gestionnaire d’événements gérés, tels que [EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True).

*MEMBRE*<br/>
Le nom de la méthode de gestionnaire d’événements à attacher au contrôle.

### <a name="remarks"></a>Notes

Cette macro crée un délégué de gestionnaire d’événements managé de type *déléguer* et du nom *membre*. Le délégué de gestionnaire d’événement managé permet à une classe native gérer les événements managés.

### <a name="example"></a>Exemple

L’exemple de code suivant montre comment appeler `MAKE_DELEGATE` pour attacher un `OnClick` Gestionnaire d’événements à un contrôle MFC `MyControl`. Pour obtenir une explication plus large du fonctionne de cette macro dans une application MFC, consultez [Comment : récepteur d’événements Windows Forms à partir de Classes C++ natives](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>Configuration requise

**En-tête :** msclr\event.h

### <a name="see-also"></a>Voir aussi

[BEGIN_DELEGATE_MAP](#begin_delegate_map)<br/>
[END_DELEGATE_MAP](#end_delegate_map)<br/>
[EVENT_DELEGATE_ENTRY](#event_delegate_entry)

