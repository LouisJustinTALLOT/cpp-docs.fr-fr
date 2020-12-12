---
description: 'En savoir plus sur : _com_ptr_t :: CreateInstance'
title: _com_ptr_t::CreateInstance
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::CreateInstance
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
ms.openlocfilehash: dd7ef236f25c22b25c9c083aea8439f5f5175d5b
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295521"
---
# <a name="_com_ptr_tcreateinstance"></a>_com_ptr_t::CreateInstance

**Spécifique à Microsoft**

Crée une nouvelle instance d’un objet en fonction d’un ou d’un `CLSID` `ProgID` .

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
`CLSID`D’un objet.

*clsidString*<br/>
Chaîne Unicode qui contient un `CLSID` (commençant par «**{**») ou un `ProgID` .

*clsidStringA*<br/>
Chaîne multioctet, utilisant la page de codes ANSI, qui contient un `CLSID` (commençant par «**{**») ou un `ProgID` .

*dwClsContext*<br/>
Contexte d'exécution du code exécutable.

*pOuter*<br/>
Externe inconnu pour l' [agrégation](../atl/aggregation.md).

## <a name="remarks"></a>Notes

Ces fonctions membres appellent `CoCreateInstance` pour créer un objet COM puis des requêtes pour le type d'interface de ce pointeur intelligent. Le pointeur résultant est alors encapsulé dans cet objet `_com_ptr_t`. `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé. Cette routine retourne le HRESULT pour indiquer la réussite ou l’échec.

- **CreateInstance (**  *rclsid* **,**  *dwClsContext*  **)** Crée une nouvelle instance en cours d’exécution d’un objet en fonction d’un `CLSID` .

- **CreateInstance (**  *clsidString* **,**  *dwClsContext*  **)** Crée une nouvelle instance en cours d’exécution d’un objet en fonction d’une chaîne Unicode qui contient un `CLSID` (commençant par «**{**») ou un `ProgID` .

- **CreateInstance (**  *clsidStringA* **,**  *dwClsContext*  **)** Crée une nouvelle instance en cours d’exécution d’un objet en fonction d’une chaîne de caractères multioctets qui contient un `CLSID` (commençant par «**{**») ou un `ProgID` . Appelle [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), qui suppose que la chaîne se trouve dans la page de codes ANSI et non dans une page de codes OEM.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_ptr_t](../cpp/com-ptr-t-class.md)
