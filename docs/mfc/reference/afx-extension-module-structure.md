---
title: AFX_EXTENSION_MODULE, Structure | Microsoft Docs
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
ms.openlocfilehash: 98486078684fe4fa8da25dd8d0c78be96be70a08
ms.sourcegitcommit: 799f9b976623a375203ad8b2ad5147bd6a2212f0
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/19/2018
ms.locfileid: "46430356"
---
# <a name="afxextensionmodule-structure"></a>AFX_EXTENSION_MODULE, structure

Le `AFX_EXTENSION_MODULE` est utilisé pendant l’initialisation de DLL d’extension MFC pour contenir l’état du module DLL d’extension MFC.

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

*bInitialized*<br/>
TRUE si le module DLL a été initialisé avec `AfxInitExtensionModule`.

*hModule*<br/>
Spécifie le handle du module DLL.

*hResource*<br/>
Spécifie le handle du module DLL ressource personnalisée.

*pFirstSharedClass*<br/>
Un pointeur vers les informations (le `CRuntimeClass` structure) sur la classe d’exécution du module DLL premier. Utilisé pour fournir le début de la liste de classe runtime.

*pFirstSharedFactory*<br/>
Un pointeur vers la fabrique d’objet du module DLL premier (un `COleObjectFactory` objet). Utilisé pour fournir le début de la liste de fabrique de classe.

## <a name="remarks"></a>Notes

Extension MFC DLL devoir faire deux choses dans leur `DllMain` (fonction) :

- Appelez [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule) et vérifiez la valeur de retournée.

- Créer un `CDynLinkLibrary` de l’objet si la DLL exporterez [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) objets ou a ses propres ressources personnalisées.

Le `AFX_EXTENSION_MODULE` structure est utilisée pour conserver une copie de l’état du module DLL, y compris une copie des classe des objets d’exécution qui ont été initialisés par la DLL d’extension MFC dans le cadre de la construction d’objet statique normale exécutée avant d’extension MFC `DllMain` est entré. Exemple :

[!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]

Les informations de module stockées dans le `AFX_EXTENSION_MODULE` structure peut être copiée dans le `CDynLinkLibrary` objet. Exemple :

[!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]

## <a name="requirements"></a>Configuration requise

**En-tête :** afx.h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables de messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)<br/>
[AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)

