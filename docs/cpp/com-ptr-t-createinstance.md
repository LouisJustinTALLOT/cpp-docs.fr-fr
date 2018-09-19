---
title: _com_ptr_t::CreateInstance | Microsoft Docs
ms.custom: ''
ms.date: 11/04/2016
ms.technology:
- cpp-language
ms.topic: language-reference
f1_keywords:
- _com_ptr_t::CreateInstance
dev_langs:
- C++
helpviewer_keywords:
- CreateInstance method [C++]
ms.assetid: ab89b0e1-9da3-4784-a079-58b17340f111
author: mikeblome
ms.author: mblome
ms.workload:
- cplusplus
ms.openlocfilehash: aa81e25b30061881dc00a401dc386647a8cdb73b
ms.sourcegitcommit: 913c3bf23937b64b90ac05181fdff3df947d9f1c
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 09/18/2018
ms.locfileid: "46094232"
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