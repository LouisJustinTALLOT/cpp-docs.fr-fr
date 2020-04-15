---
title: Initialisation d'OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: 39a6f28bfe38f254f15f441ed6305daa2cb5793e
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81373030"
---
# <a name="ole-initialization"></a>Initialisation d'OLE

Avant qu’une application puisse utiliser les services du système OLE, elle doit initialiser les DLL système OLE et vérifier que les DLL sont la version correcte. La `AfxOleInit` fonction est parascisée par les DLL du système OLE.

### <a name="ole-initialization"></a>Initialisation d'OLE

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Initialise les bibliothèques OLE.|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Appelez cette fonction dans la `InitInstance` fonction de votre objet d’application pour permettre le support pour le confinement des contrôles OLE.|

## <a name="afxenablecontrolcontainer"></a><a name="afxenablecontrolcontainer"></a>AfxEnableControlContainer

Appelez cette fonction dans la `InitInstance` fonction de votre objet d’application pour permettre le support pour le confinement des contrôles OLE.

### <a name="syntax"></a>Syntaxe

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les contrôles OLE (maintenant appelés contrôles ActiveX), voir [ActiveX Control Topics](../mfc-activex-controls.md).

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="afxoleinit"></a><a name="afxoleinit"></a>AfxOleInit AfxOleInit

Initialise le support OLE pour l’application.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Valeur de retour

Nonzero en cas de succès; 0 en cas d’échec de l’initialisation, peut-être parce que des versions incorrectes du système OLE DLL sont installées.

### <a name="remarks"></a>Notes

Appelez cette fonction pour initialiser le support OLE pour une application MFC. Lorsque cette fonction est appelée, les actions suivantes se produisent :

- Initialise la bibliothèque COM sur l’appartement actuel de la demande d’appel. Pour plus d’informations, voir [OleInitialize](/windows/win32/api/ole2/nf-ole2-oleinitialize).

- Crée un objet de filtre de message, implémentant l’interface [IMessageFilter.](/windows/win32/api/objidl/nn-objidl-imessagefilter) Ce filtre de message peut être consulté avec un appel à [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
> Si **AfxOleInit** est appelé à partir d’un MFC DLL, l’appel échouera. L’échec se produit parce que la fonction suppose que, si elle est appelée à partir d’un DLL, le système OLE a été précédemment paralé par l’application d’appel.

> [!NOTE]
> Les applications MFC doivent être paraminées en tant qu’appartement à filet unique (STA). Si vous appelez [CoInitializeEx](/windows/win32/api/combaseapi/nf-combaseapi-coinitializeex) dans votre `InitInstance` remplacement, spécifiez COINIT_APARTMENTTHREADED (plutôt que COINIT_MULTITHREADED).

### <a name="requirements"></a>Spécifications

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
