---
title: Initialisation d'OLE
ms.date: 11/04/2016
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
ms.openlocfilehash: c935dbf88b3c70cdd9ec585685bf6231ded01dde
ms.sourcegitcommit: 6052185696adca270bc9bdbec45a626dd89cdcdd
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 10/31/2018
ms.locfileid: "50623325"
---
# <a name="ole-initialization"></a>Initialisation d'OLE

Avant d’une application peut utiliser les services du système OLE, il doit initialiser les DLL système OLE et vérifiez que les DLL sont la version correcte. Le `AfxOleInit` fonction initialise les DLL système OLE.

### <a name="ole-initialization"></a>Initialisation d'OLE

|||
|-|-|
|[AfxOleInit](#afxoleinit)|Initialise les bibliothèques OLE.|
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Appelez cette fonction dans l’objet de votre application `InitInstance` (fonction) pour activer la prise en charge de la relation contenant-contenu des contrôles OLE.|

## <a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer

Appelez cette fonction dans l’objet de votre application `InitInstance` (fonction) pour activer la prise en charge de la relation contenant-contenu des contrôles OLE.

### <a name="syntax"></a>Syntaxe

```
void AfxEnableControlContainer( );
```

### <a name="remarks"></a>Notes

Pour plus d’informations sur les contrôles OLE (maintenant appelé contrôles ActiveX), consultez [rubriques du contrôle ActiveX](../mfc-activex-controls.md).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

##  <a name="afxoleinit"></a>  AfxOleInit

Initialise la prise en charge OLE pour l’application.

```
BOOL AFXAPI AfxOleInit();
```

### <a name="return-value"></a>Valeur de retour

Différent de zéro en cas de réussite ; 0 si l’initialisation échoue, probablement parce que les versions incorrectes des DLL système OLE sont installées.

### <a name="remarks"></a>Notes

Appelez cette fonction pour initialiser la prise en charge OLE pour une application MFC. Lorsque cette fonction est appelée, les actions suivantes se produisent :

- Initialise la bibliothèque COM sur l’appartement actuel de l’application appelante. Pour plus d’informations, consultez [OleInitialize](/windows/desktop/api/ole2/nf-ole2-oleinitialize).

- Crée un objet de filtre de message, mise en œuvre le [IMessageFilter](/windows/desktop/api/objidl/nn-objidl-imessagefilter) interface. Ce filtre de messages est accessible par un appel à [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).

> [!NOTE]
>  Si **AfxOleInit** est appelée à partir d’une DLL MFC, l’appel échoue. L’échec se produit parce que la fonction suppose que, si elle est appelée à partir d’une DLL, le système OLE a été précédemment initialisé par l’application appelante.

> [!NOTE]
>  Les applications MFC doivent être initialisées en tant que thread unique cloisonné (STA). Si vous appelez [CoInitializeEx](/windows/desktop/api/combaseapi/nf-combaseapi-coinitializeex) dans votre `InitInstance` substituer, spécifiez COINIT_APARTMENTTHREADED (plutôt que COINIT_MULTITHREADED).

### <a name="requirements"></a>Configuration requise

**En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi

[Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
