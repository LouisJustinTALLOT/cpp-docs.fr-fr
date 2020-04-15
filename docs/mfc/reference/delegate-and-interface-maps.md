---
title: Delegate et Interface Map Macros (MFC)
ms.date: 03/30/2017
helpviewer_keywords:
- delegate map macros [MFC]
- event map macros [MFC]
- interface map macros [MFC]
ms.assetid: 3840e642-ff7d-4bdc-998b-c7d8fc50890e
ms.openlocfilehash: e08597d024f5e3a74dcf47363ad3de0aa60cf6c0
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81365837"
---
# <a name="delegate-and-interface-map-macros"></a>Macros de délégué et de mappage d’interface

MFC prend en charge ces macros pour les cartes de délégué et d’interface :

|||
|-|-|
|[BEGIN_DELEGATE_MAP](#begin_delegate_map)|Commence une carte des délégués.|
|[BEGIN_INTERFACE_MAP](#begin_interface_map)|Commence la définition de la carte inter interface.|
|[Délégué CommandHandler](#commandhandler)|Enregistre les méthodes de rappel avec une source de commande.  |
|[END_DELEGATE_MAP](#end_delegate_map)|Termine une carte des délégués.|
|[END_INTERFACE_MAP](#end_interface_map)|Termine la carte d’interface dans le fichier d’implémentation. |
|[EVENT_DELEGATE_ENTRY](#event_delegate_entry)|Crée une entrée dans la carte des délégués.|
|[INTERFACE_PART](#interface_part)|Utilisé entre la macro BEGIN_INTERFACE_MAP et la macro END_INTERFACE_MAP pour chaque interface que votre objet prendra en charge.|
|[MAKE_DELEGATE](#make_delegate)|Attache un gestionnaire d’événements à un contrôle géré.|

## <a name="begin_delegate_map"></a><a name="begin_delegate_map"></a>BEGIN_DELEGATE_MAP

Commence une carte des délégués.

### <a name="syntax"></a>Syntaxe

```
BEGIN_DELEGATE_MAP(  CLASS );
```

### <a name="parameters"></a>Paramètres

*Classe*<br/>
La classe dans laquelle le contrôle géré est hébergé.

### <a name="remarks"></a>Notes

Cette macro marque le début d’une liste d’inscriptions déléguées, qui composent une carte des délégués. Par exemple de la façon dont cette macro est utilisée, voir [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Spécifications

**En-tête:** msclr-event.h

## <a name="begin_interface_map"></a><a name="begin_interface_map"></a>BEGIN_INTERFACE_MAP

Commence la définition de la carte inter interface lorsque lorsqu’il est utilisé dans le fichier d’implémentation.

### <a name="syntax"></a>Syntaxe

```
BEGIN_INTERFACE_MAP( theClass, baseClass )
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Classe dans laquelle la table d'interface doit être définie.

*Baseclass*<br/>
La classe d’où *la Classe* dérive.

### <a name="remarks"></a>Notes

Pour chaque interface implémentée, il y a une ou plusieurs INTERFACE_PART des invocations macro. Pour chaque agrégat que la classe utilise, il y a une INTERFACE_AGGREGATE l’invocation macro.

Pour plus d’informations sur les cartes d’interface, voir [Note technique 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="commandhandler-delegate"></a><a name="commandhandler"></a>Délégué CommandHandler

Enregistre les méthodes de rappel avec une source de commande.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandHandler(  UINT^ cmdID  );
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

### <a name="remarks"></a>Notes

Ce délégué enregistre les méthodes de rappel avec une source de commande. Lorsque vous ajoutez un délégué à l’objet source de commande, la méthode de rappel devient un gestionnaire pour les commandes provenant de la source spécifiée.

Pour plus d’informations, voir [Comment : Ajouter le routage de commande au contrôle des formulaires Windows](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md).

Pour plus d’informations sur l’utilisation des formulaires Windows, voir [à l’aide d’un contrôle de l’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxwinforms.h (défini dans l’assemblage atlmfc-lib-mfcmifc80.dll)

## <a name="commanduihandler"></a><a name="commanduihandler"></a>CommandUIHandler (en)

Enregistre les méthodes de rappel avec un message de commande de mise à jour de l’interface utilisateur.

### <a name="syntax"></a>Syntaxe

```
delegate void CommandUIHandler(  unsigned int cmdID, ICommandUI^ cmdUI);
```

### <a name="parameters"></a>Paramètres

*cmdID*<br/>
ID de la commande.

*cmdUI*<br/>
L’ID de message de commande.

### <a name="remarks"></a>Notes

Ce délégué enregistre les méthodes de rappel avec un message de commande de mise à jour de l’interface utilisateur. `CommandUIHandler`est similaire à [CommandHandler,](#commandhandler) sauf que ce délégué est utilisé avec les commandes de mise à jour d’objets d’interface utilisateur. Les commandes de mise à jour de l’interface utilisateur doivent être cartographiées en tête-à-tête avec des méthodes de gestionnaire de messages.

Pour plus d’informations sur l’utilisation des formulaires Windows, voir [à l’aide d’un contrôle de l’utilisateur de formulaire Windows dans MFC](../../dotnet/using-a-windows-form-user-control-in-mfc.md).

### <a name="requirements"></a>Spécifications

**En-tête:** afxwinforms.h (défini dans l’assemblage atlmfc-lib-mfcmifc80.dll)

## <a name="end_delegate_map"></a><a name="end_delegate_map"></a>END_DELEGATE_MAP

Termine une carte des délégués.

### <a name="syntax"></a>Syntaxe

```
END_DELEGATE_MAP();
```

### <a name="remarks"></a>Notes

Cette macro marque la fin d’une liste d’inscriptions des délégués, qui composent une carte des délégués. Par exemple de la façon dont cette macro est utilisée, voir [EVENT_DELEGATE_ENTRY](#event_delegate_entry).

### <a name="requirements"></a>Spécifications

**En-tête:** msclr-event.h

## <a name="end_interface_map"></a><a name="end_interface_map"></a>END_INTERFACE_MAP

Termine la carte d’interface dans le fichier d’implémentation.

### <a name="syntax"></a>Syntaxe

```
END_INTERFACE_MAP( )
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les cartes d’interface, voir [Note technique 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="event_delegate_entry"></a><a name="event_delegate_entry"></a>EVENT_DELEGATE_ENTRY

Crée une entrée dans la carte des délégués.

### <a name="syntax"></a>Syntaxe

```
EVENT_DELEGATE_ENTRY(MEMBER, ARG0, ARG1);
```

### <a name="parameters"></a>Paramètres

*MEMBER*<br/>
La méthode du gestionnaire d’événements à attacher au contrôle.

*ARG0*<br/>
Le premier argument de la méthode `Object^`gérée gestionnaire d’événement, tels que .

*ARG1 (arg1)*<br/>
Le deuxième argument de la méthode `EventArgs^`gérée gestionnaire d’événement, comme .

### <a name="remarks"></a>Notes

Chaque entrée sur la carte des délégués correspond à un délégué gestionnaire d’événements géré créé par [MAKE_DELEGATE](#make_delegate).

### <a name="example"></a>Exemple

L’exemple de code suivant montre comment utiliser EVENT_DELEGATE_ENTRY pour créer `OnClick` une entrée dans la carte des délégués pour le gestionnaire de l’événement; voir également l’exemple de code dans MAKE_DELEGATE. Pour plus d’informations, voir [Comment : Sink Windows Forms Events from Native CMD Classes](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
BEGIN_DELEGATE_MAP(CMyView)
   EVENT_DELEGATE_ENTRY(OnClick, System::Object^, System::EventArgs^)
END_DELEGATE_MAP()
```

### <a name="requirements"></a>Spécifications

**En-tête:** msclr-event.h

## <a name="interface_part"></a><a name="interface_part"></a>INTERFACE_PART

Utilisé entre la macro BEGIN_INTERFACE_MAP et la macro END_INTERFACE_MAP pour chaque interface que votre objet prendra en charge.

### <a name="syntax"></a>Syntaxe

```
INTERFACE_PART( theClass, iid, localClass)
```

### <a name="parameters"></a>Paramètres

*la Classe*<br/>
Nom de la classe qui contient la table d'interface.
*Iid*<br/>
L’IID qui doit être cartographié à la classe intégrée.
*LocalClass (en)*<br/>
Le nom de la classe locale.

### <a name="remarks"></a>Notes

Il vous permet de cartographier un IID à un membre de la classe indiqué par *la Classe* et *localClass*.

Pour plus d’informations sur les cartes d’interface, voir [Note technique 38](../tn038-mfc-ole-iunknown-implementation.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxwin.h

## <a name="make_delegate"></a><a name="make_delegate"></a>MAKE_DELEGATE

Attache un gestionnaire d’événements à un contrôle géré.

### <a name="syntax"></a>Syntaxe

```
MAKE_DELEGATE( DELEGATE,  MEMBER) ;
```

### <a name="parameters"></a>Paramètres

*Délégué*<br/>
Le type de délégué gestionnaire d’événements géré, comme [EventHandler](/dotnet/api/system.eventhandler).

*MEMBER*<br/>
Le nom de la méthode du gestionnaire d’événements à attacher au contrôle.

### <a name="remarks"></a>Notes

Cette macro crée un délégué gestionnaire d’événements géré de type *DELEGATE* et du nom *MEMBER*. Le délégué gestionnaire d’événements géré permet à une classe autochtone de gérer des événements gérés.

### <a name="example"></a>Exemple

L’exemple de code `MAKE_DELEGATE` suivant montre `OnClick` comment appeler pour `MyControl`joindre un gestionnaire d’événements à un contrôle MFC . Pour une explication plus large du fonctionnement de cette macro dans une application MFC, voir [Comment : Sink Windows Forms Events from Native CMD Classes](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md).

```cpp
// CMyView derives from CWinFormsView.
void CMyView::OnInitialUpdate()
{
   CWinFormsView::OnInitialUpdate();

   GetControl()->Click += MAKE_DELEGATE(System::EventHandler, OnClick);
}
```

### <a name="requirements"></a>Spécifications

**En-tête:** msclr-event.h

## <a name="see-also"></a>Voir aussi

[Comment : recevoir des événements Windows Forms de classes C++ natives](../../dotnet/how-to-sink-windows-forms-events-from-native-cpp-classes.md)<br/>
[Guide pratique pour ajouter le routage des commandes au contrôle Windows Forms](../../dotnet/how-to-add-command-routing-to-the-windows-forms-control.md)<br/>
[Macros et objet Globals](mfc-macros-and-globals.md)<br/>
