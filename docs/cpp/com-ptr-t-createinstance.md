---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: c4f6cd54b90ab5fab69f91df67a8bf60b0b658f8
ms.sourcegitcommit: 0ab61bc3d2b6cfbd52a16c6ab2b97a8ea1864f12
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/23/2019
ms.locfileid: "62399356"
---
# <a name="comptrtcreateinstance"></a>_com_ptr_t::CreateInstance

**Section spécifique à Microsoft**

Crée une nouvelle instance d’un objet doté d’un `CLSID` ou `ProgID`.

## <a name="syntax"></a>Syntaxe

```
HRESULT CreateInstance(
   const CLSID& rclsid,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCWSTR clsidString,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
HRESULT CreateInstance(
   LPCSTR clsidStringA,
   IUnknown* pOuter=NULL,
   DWORD dwClsContext = CLSCTX_ALL
) throw( );
```

#### <a name="parameters"></a>Paramètres

*rclsid*<br/>
Le `CLSID` d’un objet.

*clsidString*<br/>
Une chaîne Unicode qui contient un `CLSID` (en commençant par «**{**») ou un `ProgID`.

*clsidStringA*<br/>
Chaîne multioctet, à l’aide de la page de codes ANSI, qui contient un `CLSID` (en commençant par «**{**») ou un `ProgID`.

*dwClsContext*<br/>
Contexte d'exécution du code exécutable.

*pOuter*<br/>
Inconnu externe pour [agrégation](../atl/aggregation.md).

## <a name="remarks"></a>Notes

Ces fonctions membres appellent `CoCreateInstance` pour créer un objet COM puis des requêtes pour le type d'interface de ce pointeur intelligent. Le pointeur résultant est alors encapsulé dans cet objet `_com_ptr_t`. `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé. Cette routine retourne le HRESULT pour indiquer la réussite ou l’échec.

- **CreateInstance (***rclsid* **,***dwClsContext***)** crée une nouvelle instance en cours d’exécution d’un objet doté d’un `CLSID`.

- **CreateInstance (***clsidString* **,***dwClsContext***)** crée une nouvelle instance en cours d’exécution d’un objet doté d’un Chaîne Unicode qui contient un `CLSID` (en commençant par «**{**») ou un `ProgID`.

- **CreateInstance (***clsidStringA* **,***dwClsContext***)** crée une nouvelle instance en cours d’exécution d’un objet doté d’un chaîne de caractères multioctets qui contient un `CLSID` (en commençant par «**{**») ou un `ProgID`. Appels [MultiByteToWideChar](/windows/desktop/api/stringapiset/nf-stringapiset-multibytetowidechar), ce qui suppose que la chaîne est dans la page de codes ANSI plutôt que dans une page de codes OEM.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)