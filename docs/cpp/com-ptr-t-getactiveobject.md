---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: f13a42878392f63096cdfcb405f3f91cc0efe451
ms.sourcegitcommit: fcb48824f9ca24b1f8bd37d647a4d592de1cc925
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/15/2019
ms.locfileid: "69498898"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Section spécifique à Microsoft**

Attache à une instance existante d’un objet à partir d' `CLSID` un `ProgID`ou d’un.

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
`CLSID` D’un objet.

*clsidString*<br/>
Chaîne Unicode qui contient un `CLSID` (commençant par « **{** ») ou un. `ProgID`

*clsidStringA*<br/>
Chaîne multioctet, utilisant la page de codes ANSI, qui contient un `CLSID` (commençant par « **{** ») ou un. `ProgID`

## <a name="remarks"></a>Notes

Ces fonctions membres appellent **GetActiveObject** pour récupérer un pointeur vers un objet en cours d’exécution qui a été inscrit avec OLE, puis interroge le type d’interface de ce pointeur intelligent. Le pointeur résultant est alors encapsulé dans cet objet `_com_ptr_t`. `Release`est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé. Cette routine retourne le HRESULT pour indiquer la réussite ou l’échec.

- **GetActiveObject (** `rclsid` **)** s’attache à une instance existante d’un objet en fonction `CLSID`d’un.

- **GetActiveObject (** `clsidString` **)** s’attache à une instance existante d’un objet en fonction d’une chaîne Unicode qui contient `CLSID` un (commençant par « **{** ») ou `ProgID`un.

- **GetActiveObject (** `clsidStringA` **)** s’attache à une instance existante d’un objet en fonction d’une chaîne de caractères multioctets qui `CLSID` contient un (commençant par « **{** ») `ProgID`ou un. Appelle [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), qui suppose que la chaîne se trouve dans la page de codes ANSI et non dans une page de codes OEM.

**FIN de la section spécifique à Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)