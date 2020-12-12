---
description: 'En savoir plus sur : initialisation d’OLE'
title: Initialisation d'OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 0efed4fefe62b720852905b6eed44501d4369efa
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97218990"
---
# <a name="ole-initialization"></a>Initialisation d'OLE

Pour qu’une application puisse utiliser les services système OLE, elle doit initialiser les DLL système OLE et vérifier que la version des dll est correcte. La `AfxOleInit` fonction initialise les DLL système OLE.

### <a name="ole-initialization"></a>Initialisation d'OLE

|Nom|Description|
|-|-|
|[AfxOleInit](#afxoleinit)|Initialise les bibliothèques OLE.|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Appelez cette fonction dans la fonction de votre objet application `InitInstance` pour activer la prise en charge de la relation contenant-contenu des contrôles OLE.|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer (

Appelez cette fonction dans la fonction de votre objet application `InitInstance` pour activer la prise en charge de la relation contenant-contenu des contrôles OLE.

### <a name="syntax"></a>Syntaxe

```cpp
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les contrôles OLE (désormais appelés contrôles ActiveX), consultez les [rubriques relatives](../mfc-activex-controls.md)aux contrôles ActiveX.

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="afxoleinit"></a><a name="afxoleinit"></a> AfxOleInit

Initialise la prise en charge OLE pour l’application.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Valeur renvoyée

Valeur différente de zéro en cas de réussite ; 0 si l’initialisation échoue, peut-être parce que des versions incorrectes des DLL système OLE sont installées.

### <a name="remarks"></a>Notes

Appelez cette fonction pour initialiser la prise en charge OLE pour une application MFC. Lorsque cette fonction est appelée, les actions suivantes se produisent :

- Initialise la bibliothèque COM sur le cloisonnement actuel de l’application appelante. Pour plus d’informations, consultez [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize).

- Crée un objet de filtre de messages, en implémentant l’interface [IMessageFilter](/windows/win32/api/objidl/nn-objidl-imessagefilter) . Ce filtre de messages est accessible à l’aide d’un appel à [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
> Si **AfxOLEInit** est appelé à partir d’une DLL MFC, l’appel échoue. L’échec se produit parce que la fonction suppose que, s’il est appelé à partir d’une DLL, le système OLE a été précédemment initialisé par l’application appelante.

> [!NOTE]
> Les applications MFC doivent être initialisées en tant que thread unique cloisonné (STA). Si vous appelez [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) dans votre `InitInstance` remplacement, spécifiez COINIT_APARTMENTTHREADED (plutôt que COINIT_MULTITHREADED).

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
