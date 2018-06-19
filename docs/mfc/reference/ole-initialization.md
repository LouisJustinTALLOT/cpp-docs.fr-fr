---
title: L’initialisation d’OLE | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- afxdisp/AfxOleInit
- afxdisp/AfxEnableControlContainer
dev_langs:
- C++
helpviewer_keywords:
- OLE initialization
ms.assetid: aa8a54a7-24c3-4344-b2c6-dbcf6084fa31
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: b8224cf27313b056b95990f514e02eb9d9c08cad
ms.sourcegitcommit: 76b7653ae443a2b8eb1186b789f8503609d6453e
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 05/04/2018
ms.locfileid: "33374722"
---
# <a name="ole-initialization"></a>Initialisation d'OLE
Avant d’une application peut utiliser les services du système OLE, il doit initialiser les DLL système OLE et vérifiez que les DLL sont la version correcte. Le **AfxOleInit** fonction initialise les DLL système OLE.  
  
### <a name="ole-initialization"></a>Initialisation d'OLE  
  
|||  
|-|-|  
|[AfxOleInit](#afxoleinit)|Initialise les bibliothèques OLE.| 
|[AfxEnableControlContainer](#afxenablecontrolcontainer)|Appelez cette fonction dans l’objet de votre application `InitInstance` fonction pour activer la prise en charge de la relation contenant-contenu des contrôles OLE.| 


## <a name="afxenablecontrolcontainer"></a> AfxEnableControlContainer
Appelez cette fonction dans l’objet de votre application `InitInstance` fonction pour activer la prise en charge de la relation contenant-contenu des contrôles OLE.  
   
### <a name="syntax"></a>Syntaxe    
```
void AfxEnableControlContainer( );  
```  
   
### <a name="remarks"></a>Notes  
 Pour plus d’informations sur les contrôles OLE (désormais appelés contrôles ActiveX), consultez [rubriques relatives au contrôle ActiveX](../mfc-activex-controls.md).  
   
### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h  

  
##  <a name="afxoleinit"></a>  AfxOleInit  
 Initialise la prise en charge OLE pour l’application.  
  
``` 
BOOL AFXAPI AfxOleInit(); 
```  
  
### <a name="return-value"></a>Valeur de retour  
 Différent de zéro si l’opération a réussi ; 0 si l’initialisation échoue, probablement parce que les versions incorrectes des DLL système OLE sont installées.  
  
### <a name="remarks"></a>Notes  
 Appelez cette fonction pour initialiser la prise en charge OLE pour une application MFC. Lorsque cette fonction est appelée, les actions suivantes se produisent :  
  
-   Initialise la bibliothèque COM sur le cloisonnement actuel de l’application appelante. Pour plus d’informations, consultez [OleInitialize](http://msdn.microsoft.com/library/windows/desktop/ms690134).  
  
-   Crée un objet de filtre de message, mise en œuvre le [IMessageFilter](http://msdn.microsoft.com/library/windows/desktop/ms693740) interface. Ce filtre de messages est accessible par un appel à [AfxOleGetMessageFilter](application-control.md#afxolegetmessagefilter).  
  
> [!NOTE]
>  Si **AfxOleInit** est appelée à partir d’une DLL MFC, l’appel échoue. L’échec se produit parce que la fonction suppose que, si elle est appelée à partir d’une DLL, le système OLE a été précédemment initialisé par l’application appelante.  
  
> [!NOTE]
>  Les applications MFC doivent être initialisées dans un thread unique cloisonné (STA). Si vous appelez [CoInitializeEx](http://msdn.microsoft.com/library/windows/desktop/ms695279) dans votre `InitInstance` remplacer, spécifiez `COINIT_APARTMENTTHREADED` (au lieu de `COINIT_MULTITHREADED`). Pour plus d’informations, consultez PRB : Application MFC ne répond plus lorsque vous initialisez l’Application en tant qu’un multithread cloisonné (828643) à [ http://support.microsoft.com/default.aspxscid=kb; en-us ; 828643](http://support.microsoft.com/default.aspxscid=kb;en-us;828643).  

### <a name="requirements"></a>Spécifications  
 **En-tête :** afxdisp.h

## <a name="see-also"></a>Voir aussi  
 [Macros et objet Globals](../../mfc/reference/mfc-macros-and-globals.md)
