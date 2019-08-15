---
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: 82b180b3f40683495ed2cfa284bdae8e1afaef9e
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498664"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Section spécifique à Microsoft**

Crée une nouvelle instance d’un objet en fonction `CLSID` d' `ProgID`un ou d’un.

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
`CLSID` D’un objet.

*clsidString*<br/>
Chaîne Unicode qui contient un `CLSID` (commençant par « **{** ») ou un. `ProgID`

*clsidStringA*<br/>
Chaîne multioctet, utilisant la page de codes ANSI, qui contient un `CLSID` (commençant par « **{** ») ou un. `ProgID`

*dwClsContext*<br/>
Contexte d'exécution du code exécutable.

*pOuter*<br/>
Externe inconnu pour l' [agrégation](../atl/aggregation.md).

## <a name="remarks"></a>Notes

Ces fonctions membres appellent `CoCreateInstance` pour créer un objet COM puis des requêtes pour le type d'interface de ce pointeur intelligent. Le pointeur résultant est alors encapsulé dans cet objet `_com_ptr_t`. `Release`est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé. Cette routine retourne le HRESULT pour indiquer la réussite ou l’échec.

- **CreateInstance (** *rclsid* **,** *dwClsContext* **)** Crée une nouvelle instance en cours d’exécution d’un `CLSID`objet en fonction d’un.

- **CreateInstance (** *clsidString* **,** *dwClsContext* **)** Crée une nouvelle instance en cours d’exécution d’un objet en fonction d’une chaîne `CLSID` Unicode qui contient un (commençant par « **{** ») ou un `ProgID`.

- **CreateInstance (** *clsidStringA* **,** *dwClsContext* **)** Crée une nouvelle instance en cours d’exécution d’un objet en fonction d’une chaîne de caractères `CLSID` multioctets qui contient un (commençant par « `ProgID` **{** ») ou un. Appelle [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), qui suppose que la chaîne se trouve dans la page de codes ANSI et non dans une page de codes OEM.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)