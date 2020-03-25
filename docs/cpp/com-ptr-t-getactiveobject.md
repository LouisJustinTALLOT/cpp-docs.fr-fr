---
title: _com_ptr_t::GetActiveObject
ms.date: 11/04/2016
f1_keywords:
- _com_ptr_t::GetActiveObject
helpviewer_keywords:
- GetActiveObject method [C++]
ms.assetid: 2fa94853-0410-4620-91f2-136dae923f9f
ms.openlocfilehash: ea8059a039b77811dd54d4a4937ad746b7ca0937
ms.sourcegitcommit: 857fa6b530224fa6c18675138043aba9aa0619fb
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 03/24/2020
ms.locfileid: "80170799"
---
# <a name="_com_ptr_tgetactiveobject"></a>_com_ptr_t::GetActiveObject

**Section spécifique de Microsoft**

Attache à une instance existante d’un objet en fonction d’un `CLSID` ou d’un `ProgID`.

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
`CLSID` d’un objet.

*clsidString*<br/>
Chaîne Unicode qui contient un `CLSID` (commençant par « **{** ») ou un `ProgID`.

*clsidStringA*<br/>
Chaîne multioctet, utilisant la page de codes ANSI, qui contient un `CLSID` (commençant par « **{** ») ou un `ProgID`.

## <a name="remarks"></a>Notes

Ces fonctions membres appellent **GetActiveObject** pour récupérer un pointeur vers un objet en cours d’exécution qui a été inscrit avec OLE, puis interroge le type d’interface de ce pointeur intelligent. Le pointeur résultant est alors encapsulé dans cet objet `_com_ptr_t`. `Release` est appelé pour décrémenter le décompte de références pour le pointeur précédemment encapsulé. Cette routine retourne le HRESULT pour indiquer la réussite ou l’échec.

- **GetActiveObject (** `rclsid` **)** Attache à une instance existante d’un objet en fonction d’un `CLSID`.

- **GetActiveObject (** `clsidString` **)** Attache à une instance existante d’un objet en fonction d’une chaîne Unicode qui contient un `CLSID` (commençant par « **{** ») ou un `ProgID`.

- **GetActiveObject (** `clsidStringA` **)** Attache à une instance existante d’un objet en fonction d’une chaîne de caractères multioctets qui contient un `CLSID` (commençant par « **{** ») ou un `ProgID`. Appelle [MultiByteToWideChar](/windows/win32/api/stringapiset/nf-stringapiset-multibytetowidechar), qui suppose que la chaîne se trouve dans la page de codes ANSI et non dans une page de codes OEM.

**Fin de la section spécifique de Microsoft**

## <a name="see-also"></a>Voir aussi

[_com_ptr_t, classe](../cpp/com-ptr-t-class.md)
