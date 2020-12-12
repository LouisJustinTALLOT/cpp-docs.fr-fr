---
description: 'En savoir plus sur : structure AFX_EXTENSION_MODULE'
title: AFX_EXTENSION_MODULE, structure
ms.date: 11/04/2016
f1_keywords:
- AFX_EXTENSION_MODULE
helpviewer_keywords:
- AFX_EXTENSION_MODULE structure [MFC]
ms.assetid: b85a989c-d0c5-4b28-b53c-dad45b75704e
ms.openlocfilehash: d3a5abd449f13a06aa5d7388b2dd2926a6011973
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97248227"
---
# <a name="afx_extension_module-structure"></a>AFX_EXTENSION_MODULE, structure

`AFX_EXTENSION_MODULE`Est utilisé pendant l’initialisation des dll d’extension MFC pour contenir l’état du module dll d’extension MFC.

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
TRUE si le module DLL a été initialisé avec `AfxInitExtensionModule` .

*hModule*<br/>
Spécifie le handle du module DLL.

*hResource*<br/>
Spécifie le handle du module de ressource personnalisé DLL.

*pFirstSharedClass*<br/>
Pointeur vers les informations (la `CRuntimeClass` structure) à propos de la première classe Runtime du module dll. Utilisé pour fournir le début de la liste de classes Runtime.

*pFirstSharedFactory*<br/>
Pointeur vers la première fabrique d’objets du module DLL (un `COleObjectFactory` objet). Utilisé pour indiquer le début de la liste des fabriques de classes.

## <a name="remarks"></a>Notes

Les dll d’extension MFC doivent faire deux choses dans leur `DllMain` fonction :

- Appelez [AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule) et vérifiez la valeur de retour.

- Créez un `CDynLinkLibrary` objet si la dll exporte des objets [CRuntimeClass](../../mfc/reference/cruntimeclass-structure.md) ou possède ses propres ressources personnalisées.

La `AFX_EXTENSION_MODULE` structure est utilisée pour stocker une copie de l’état du module dll d’extension MFC, y compris une copie des objets de classe d’exécution qui ont été initialisés par la dll d’extension MFC dans le cadre de la construction d’objet statique normale exécutée avant l' `DllMain` entrée. Par exemple :

[!code-cpp[NVC_MFC_DLL#2](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_1.cpp)]

Les informations de module stockées dans la `AFX_EXTENSION_MODULE` structure peuvent être copiées dans l' `CDynLinkLibrary` objet. Par exemple :

[!code-cpp[NVC_MFC_DLL#5](../../atl-mfc-shared/codesnippet/cpp/afx-extension-module-structure_2.cpp)]

## <a name="requirements"></a>Spécifications

**En-tête :** AFX. h

## <a name="see-also"></a>Voir aussi

[Structures, styles, rappels et tables des messages](../../mfc/reference/structures-styles-callbacks-and-message-maps.md)<br/>
[AfxInitExtensionModule](extension-dll-macros.md#afxinitextensionmodule)<br/>
[AfxTermExtensionModule](extension-dll-macros.md#afxtermextensionmodule)
