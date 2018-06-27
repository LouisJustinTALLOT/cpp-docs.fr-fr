---
title: AFX_EXTENSION_MODULE, Structure | Documents Microsoft
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-mfc
ms.topic: reference
f1_keywords:
- AFX_EXTENSION_MODULE
dev_langs:
- C++
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: e741f172d0dfe528a166fad087460fd9ae18c0f3
ms.sourcegitcommit: c6b095c5f3de7533fd535d679bfee0503e5a1d91
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 06/26/2018
ms.locfileid: "36951180"
---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE, structure
Le `AFX_EXTENSION_MODULE` utilisée lors de l’initialisation de DLL d’extension MFC pour conserver l’état du module DLL d’extension MFC.  
  
## <a name="syntax"></a>Syntaxe  
  
```  
struct AFX_EXTENSION_MODULE  
{  
    BOOL bInitialized;  
    HMODULE hModule;  
    HMODULE hResource;  
    CRuntimeClass* pFirstSharedClass;  
    COleObjectFactory* pFirstSharedFactory;  
};  
```  
  
#### <a name="parameters"></a>Paramètres  
 *bInitialized*  
 **TRUE** si le module DLL a été initialisé avec `AfxInitExtensionModule`.  
  
 *hModule*  
 Spécifie le handle du module DLL.  
  
 *hResource*  
 Spécifie le handle du module DLL ressource personnalisée.  
  
 *pFirstSharedClass*  
 Un pointeur vers les informations (le `CRuntimeClass` structure) sur la classe d’exécution du module DLL premier. Utilisé pour fournir le début de la liste de la classe runtime.  
  
 *pFirstSharedFactory*  
 Un pointeur vers la fabrique d’objet du module DLL premier (un `COleObjectFactory` objet). Utilisé pour fournir le début de la liste de fabrique de classe.  
  
## <a name="remarks"></a>Notes  
 L’extension MFC DLL devoir faire deux choses dans leur `DllMain` (fonction) :  
  
-   Appelez [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule) et vérifiez la valeur de retour.  
  
-   Créer un `CDynLinkLibrary` exportez si la DLL de l’objet [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) des objets ou possède ses propres ressources personnalisées.  
  
 Le `AFX_EXTENSION_MODULE` structure est utilisée pour conserver une copie de l’état du module DLL, y compris une copie des objets de classe runtime qui ont été initialisé par la DLL d’extension MFC dans le cadre de la construction d’objet statique normal exécutée avant d’extension MFC `DllMain` est entrée. Exemple :  
  
 [!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]  
  
 Les informations du module stockées dans le `AFX_EXTENSION_MODULE` structure peut être copiée dans le `CDynLinkLibrary` objet. Exemple :  
  
 [!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]  
  
## <a name="requirements"></a>Configuration requise  
 **En-tête :** afx.h  
  
## <a name="see-also"></a>Voir aussi  
 [Structures, Styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)   
 [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)   
 [AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)

