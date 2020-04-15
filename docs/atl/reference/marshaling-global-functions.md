---
title: Marshaling Global Functions
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: b839e93b6251a09ce79df60a49b4054d1af76cc9
ms.sourcegitcommit: c123cc76bb2b6c5cde6f4c425ece420ac733bf70
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 04/14/2020
ms.locfileid: "81326262"
---
# <a name="marshaling-global-functions"></a>Marshaling Global Functions

Ces fonctions fournissent un soutien pour le marshaling et la conversion des données de marshaling en pointeurs d’interface.

> [!IMPORTANT]
> Les fonctions énumérées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|||
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Communiqués les données `IStream` du maréchal et le pointeur.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Crée un nouvel objet de flux et marshals le pointeur d’interface spécifié.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|Convertit les données de marshaling d’un flux en pointeur d’interface.|

## <a name="requirements"></a>Conditions requises :

**En-tête:** atlbase.h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a>AtlFreeMarshalStream

Libère les données de marshaling dans le flux, puis libère le pointeur de flux.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
[dans] Un pointeur `IStream` à l’interface sur le flux utilisé pour le marshaling.

### <a name="example"></a>Exemple

Voir l’exemple pour [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a>AtlMarshalPtrInProc

Crée un objet de flux, écrit le CLSID du proxy dans le flux, puis marshale le pointeur d'interface spécifié en écrivant les données nécessaires pour initialiser le proxy dans le flux.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Paramètres

*Punk*<br/>
[dans] Un pointeur à l’interface à mobiliser.

*Iid*<br/>
[dans] Le GUID de l’interface étant mobilisé.

*ppStream*<br/>
[out] Un pointeur `IStream` à l’interface sur le nouvel objet de flux utilisé pour le marshaling.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="remarks"></a>Notes

Le drapeau MSHLFLAGS_TABLESTRONG est fixé de sorte que le pointeur peut être monté sur plusieurs ruisseaux. Le pointeur peut également être non-ramshaled plusieurs fois.

En cas d’échec du marshaling, le pointeur du flux est libéré.

`AtlMarshalPtrInProc`ne peut être utilisé que sur un pointeur à un objet en cours.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a>AtlUnmarshalPtr

Convertit les données de marshaling du flux en un pointeur d'interface qui peut être utilisé par le client.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
[dans] Un pointeur pour le ruisseau étant non-ramshaled.

*Iid*<br/>
[dans] Le GUID de l’interface étant non-notée.

*ppUnk*<br/>
[out] Un pointeur à l’interface non ramshalée.

### <a name="return-value"></a>Valeur de retour

Une valeur HRESULT standard.

### <a name="example"></a>Exemple

Voir l’exemple pour [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
