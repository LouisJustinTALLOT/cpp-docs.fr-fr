---
title: Délégués et macros de mappage d’interface (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: 8f48b916f7130551fc8d4da5bb2ebc75d8d728d5
ms.sourcegitcommit: 7ecd91d8ce18088a956917cdaf3a3565bd128510
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/16/2020
ms.locfileid: "79421393"
---
# <a name="delegate-and-interface-map-macros"></a>Macros de délégué et de mappage d’interface

MFC prend en charge les macros suivantes pour les mappages de délégués et d’interfaces :

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Commence un mappage de délégué.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Commence la définition de la carte avec interfacement.|
|[Délégué CommandHandler](#commandhandler)|Inscrit les méthodes de rappel avec une source de commande.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Termine un mappage de délégué.|
|[END_INTERFACE_MAP](#end_interface_map)|Termine le mappage d’interface dans le fichier d’implémentation. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Crée une entrée dans le mappage de délégué.|
|[INTERFACE_PART](#interface_part)|Utilisé entre la macro BEGIN_INTERFACE_MAP et la macro END_INTERFACE_MAP pour chaque interface que votre objet prend en charge.|
|[MAKE_DELEGATE](#make_delegate)|Attache un gestionnaire d’événements à un contrôle managé.|

## <a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

Commence un mappage de délégué.

### <a name="syntax"></a>Syntaxe

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Paramètres

*TYPE*<br/>
Classe dans laquelle le contrôle managé est hébergé.

### <a name="remarks"></a>Notes

Cette macro marque le début d’une liste d’entrées de délégué, qui composent un mappage de délégué. Pour obtenir un exemple de la façon dont cette macro est utilisée, consultez [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Spécifications

**En-tête :** msclr\event.h

##  <a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Commence la définition de la carte avec interfacement lorsqu’elle est utilisée dans le fichier d’implémentation.

### <a name="syntax"></a>Syntaxe

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Classe dans laquelle la table d'interface doit être définie.

*baseClass*<br/>
Classe à partir de laquelle dérive *les* .

### <a name="remarks"></a>Notes

Pour chaque interface implémentée, il existe un ou plusieurs INTERFACE_PART appel de macro. Pour chaque agrégat utilisé par la classe, il existe un INTERFACE_AGGREGATE appel de macro.

Pour plus d’informations sur les cartes d’interface, consultez la [note technique 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="commandhandler"></a>Délégué CommandHandler

Inscrit les méthodes de rappel avec une source de commande.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

### <a name="remarks"></a>Notes

Ce délégué inscrit des méthodes de rappel avec une source de commande. Quand vous ajoutez un délégué à l’objet source de commande, la méthode de rappel devient un gestionnaire pour les commandes provenant de la source spécifiée.

Pour plus d’informations, consultez [Comment : ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms. h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

##  <a name="commanduihandler"></a>CommandUIHandler

Inscrit les méthodes de rappel avec un message de commande de mise à jour de l’interface utilisateur.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

*cmdUI*<br/>
ID du message de commande.

### <a name="remarks"></a>Notes

Ce délégué inscrit des méthodes de rappel avec un message de commande de mise à jour de l’interface utilisateur. `CommandUIHandler` est semblable à [CommandHandler](#commandhandler) , à ceci près que ce délégué est utilisé avec les commandes de mise à jour d’objet d’interface utilisateur. Les commandes de mise à jour de l’interface utilisateur doivent être mappées un-à-un avec les méthodes de gestionnaire de messages.

Pour plus d’informations sur l’utilisation de Windows Forms, consultez [utilisation d’un contrôle utilisateur Windows Form dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwinforms. h (défini dans l’assembly atlmfc\lib\mfcmifc80.dll)

##  <a name="end_delegate_map"></a>END_DELEGATE_MAP

Termine un mappage de délégué.

### <a name="syntax"></a>Syntaxe

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Notes

Cette macro marque la fin d’une liste d’entrées de délégué qui composent un mappage de délégué. Pour obtenir un exemple de la façon dont cette macro est utilisée, consultez [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Spécifications

**En-tête :** msclr\event.h

##  <a name="end_interface_map"></a>END_INTERFACE_MAP

Termine le mappage d’interface dans le fichier d’implémentation.

### <a name="syntax"></a>Syntaxe

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les cartes d’interface, consultez la [note technique 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Crée une entrée dans le mappage de délégué.

### <a name="syntax"></a>Syntaxe

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Paramètres

*MEMBRE*<br/>
Méthode de gestionnaire d’événements à attacher au contrôle.

*ARG0*<br/>
Premier argument de la méthode de gestionnaire d’événements managée, tel que `Object^`.

*ARG1*<br/>
Deuxième argument de la méthode de gestionnaire d’événements managée, tel que `EventArgs^`.

### <a name="remarks"></a>Notes

Chaque entrée dans le mappage de délégué correspond à un délégué de gestionnaire d’événements managé créé par [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Exemple

L’exemple de code suivant montre comment utiliser EVENT_DELEGATE_ENTRY pour créer une entrée dans le mappage de délégué pour le gestionnaire d’événements `OnClick` ; Consultez également l’exemple de code dans MAKE_DELEGATE. Pour plus d’informations, consultez [Comment : recevoir des événements de Windows Forms C++ à partir de classes natives](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Spécifications

**En-tête :** msclr\event.h

##  <a name="interface_part"></a>INTERFACE_PART

Utilisé entre la macro BEGIN_INTERFACE_MAP et la macro END_INTERFACE_MAP pour chaque interface que votre objet prend en charge.

### <a name="syntax"></a>Syntaxe

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Paramètres

*Les*<br/>
Nom de la classe qui contient la table d'interface.
*vaut*<br/>
IID qui doit être mappé à la classe incorporée.
*localClass*<br/>
Nom de la classe locale.

### <a name="remarks"></a>Notes

Elle vous permet de mapper un IID à un membre de la classe indiquée par *les* et *localClass*.

Pour plus d’informations sur les cartes d’interface, consultez la [note technique 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

##  <a name="make_delegate"></a>MAKE_DELEGATE

Attache un gestionnaire d’événements à un contrôle managé.

### <a name="syntax"></a>Syntaxe

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Paramètres

*DISPOSER*<br/>
Type du délégué de gestionnaire d’événements managé, tel que [EventHandler](assetId:///T:System.EventHandler?qualifyHint=False&autoUpgrade=True).

*MEMBRE*<br/>
Nom de la méthode de gestionnaire d’événements à attacher au contrôle.

### <a name="remarks"></a>Notes

Cette macro crée un délégué de gestionnaire d’événements managés de type *Delegate* et du *membre*Name. Le délégué de gestionnaire d’événements managé permet à une classe native de gérer des événements managés.

### <a name="example"></a>Exemple

L’exemple de code suivant montre comment appeler `MAKE_DELEGATE` pour attacher un gestionnaire d’événements `OnClick` à un `MyControl`de contrôle MFC. Pour plus d’explications sur le fonctionnement de cette macro dans une application MFC, consultez Guide pratique [pour recevoir des événements de Windows Forms C++ à partir de classes natives](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>Spécifications

**En-tête :** msclr\event.h

## <a name="see-also"></a>Voir aussi

[Guide pratique pour recevoir des événements Windows Forms de classes C++ natives](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Macros et globales](mfc-macros-and-globals.md)<br/>
