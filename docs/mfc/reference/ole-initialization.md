---
title: Initialisation d'OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 6860697dd3adbe26197dd9075e84f402029e00a5
ms.sourcegitcommit: 3e8fa01f323bc5043a48a0c18b855d38af3648d4
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/06/2020
ms.locfileid: "78855686"
---
# <a name="ole-initialization"></a>Initialisation d'OLE

Pour qu’une application puisse utiliser les services système OLE, elle doit initialiser les DLL système OLE et vérifier que la version des dll est correcte. La fonction `AfxOleInit` initialise les DLL système OLE.

### <a name="ole-initialization"></a>Initialisation d'OLE

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Initialise les bibliothèques OLE.|
|[AfxEnableControlContainer (](#afxenablecontrolcontainer)|Appelez cette fonction dans la fonction `InitInstance` de votre objet application pour activer la prise en charge de la relation contenant-contenu des contrôles OLE.|

## <a name="afxenablecontrolcontainer"></a>AfxEnableControlContainer (

Appelez cette fonction dans la fonction `InitInstance` de votre objet application pour activer la prise en charge de la relation contenant-contenu des contrôles OLE.

### <a name="syntax"></a>Syntaxe

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les contrôles OLE (désormais appelés contrôles ActiveX), consultez les [rubriques relatives](../mfc-activex-controls.md)aux contrôles ActiveX.

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

##  <a name="afxoleinit"></a>AfxOleInit

Initialise la prise en charge OLE pour l’application.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Valeur de retour

Valeur différente de zéro en cas de réussite ; 0 si l’initialisation échoue, peut-être parce que des versions incorrectes des DLL système OLE sont installées.

### <a name="remarks"></a>Notes

Appelez cette fonction pour initialiser la prise en charge OLE pour une application MFC. Lorsque cette fonction est appelée, les actions suivantes se produisent :

- Initialise la bibliothèque COM sur le cloisonnement actuel de l’application appelante. Pour plus d’informations, consultez [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize).

- Crée un objet de filtre de messages, en implémentant l’interface [IMessageFilter](/windows/win32/api/objidl/nn-objidl-imessagefilter) . Ce filtre de messages est accessible à l’aide d’un appel à [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
>  Si **AfxOLEInit** est appelé à partir d’une DLL MFC, l’appel échoue. L’échec se produit parce que la fonction suppose que, s’il est appelé à partir d’une DLL, le système OLE a été précédemment initialisé par l’application appelante.

> [!NOTE]
>  Les applications MFC doivent être initialisées en tant que thread unique cloisonné (STA). Si vous appelez [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) dans votre `InitInstance` remplacement, spécifiez COINIT_APARTMENTTHREADED (plutôt que COINIT_MULTITHREADED).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et globales](../../mfc/reference/mfc-macros-and-globals.md)
