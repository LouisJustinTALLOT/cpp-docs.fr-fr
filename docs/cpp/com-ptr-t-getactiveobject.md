---
description: 'En savoir plus sur : _com_ptr_t :: GetActiveObject'
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: 96784e73d91d7be4b0674e09278183fc62e60af2
ms.sourcegitcommit: d6af41e42699628c3e2e6063ec7b03931a49a098
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 12/11/2020
ms.locfileid: "97295469"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Spécifique à Microsoft**

Attache à une instance existante d’un objet à partir d’un ou d’un `CLSID` `ProgID` .

## <a name="syntax"></a>Syntaxe

```
HRESULT GetActiveObject(
   const CLSID& rclsid
) throw( );
HRESULT GetActiveObject(
   LPCWSTR clsidString
) throw( );
HRESULT GetActiveObject(
   LPCSTR clsidStringA
) throw( );
```

#### <a name="parameters"></a>Paramètres

*rclsid*<br/>
`CLSID`D’un objet.

*clsidString*<br/>
Chaîne Unicode qui contient un `CLSID` (commençant par «**{**») ou un `ProgID` .

*clsidStringA*<br/>
Chaîne multioctet, utilisant la page de codes ANSI, qui contient un `CLSID` (commençant par «**{**») ou un `ProgID` .

## <a name="remarks"></a>Notes

Ces fonctions membres appellent **GetActiveObject** pour récupérer un pointeur vers un objet en cours d’exécution qui a été inscrit avec OLE, puis interroge le type d’interface de ce pointeur intelligent. Le pointeur résultant est alors encapsulé dans cet objet `_com_ptr_t`. `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé. Cette routine retourne le HRESULT pour indiquer la réussite ou l’échec.

- **GetActiveObject (** `rclsid` **)** s’attache à une instance existante d’un objet en fonction d’un `CLSID` .    

- **GetActiveObject (** `clsidString` **)** s’attache à une instance existante d’un objet en fonction d’une chaîne Unicode qui contient un `CLSID` (commençant par «**{**») ou un `ProgID` .    

- **GetActiveObject (** `clsidStringA` **)** s’attache à une instance existante d’un objet en fonction d’une chaîne de caractères multioctets qui contient un `CLSID` (commençant par «**{**») ou un `ProgID` .     Appelle [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), qui suppose que la chaîne se trouve dans la page de codes ANSI et non dans une page de codes OEM.

**FIN spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[Classe _com_ptr_t](../cpp/com-ptr-t-class.md)
