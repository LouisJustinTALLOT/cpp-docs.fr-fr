---
title: Marshaling des fonctions globales
ms.date: 11/04/2016
f1_keywords:
- atlbase/ATL::AtlFreeMarshalStream
- atlbase/ATL::AtlMarshalPtrInProc
- atlbase/ATL::AtlUnmarshalPtr
ms.assetid: 877100b5-6ad9-44c5-a2e0-09414f1720d0
ms.openlocfilehash: 79b19b613fbae49c0f8338dcadd2225e092fb371
ms.sourcegitcommit: ec6dd97ef3d10b44e0fedaa8e53f41696f49ac7b
ms.translationtype: MT
ms.contentlocale: fr-FR
ms.lasthandoff: 08/25/2020
ms.locfileid: "88835322"
---
# <a name="marshaling-global-functions"></a>Marshaling des fonctions globales

Ces fonctions assurent la prise en charge du marshaling et de la conversion des données de marshaling en pointeurs d’interface.

> [!IMPORTANT]
> Les fonctions listées dans le tableau suivant ne peuvent pas être utilisées dans les applications qui s’exécutent dans le Windows Runtime.

|Nom|Description|
|-|-|
|[AtlFreeMarshalStream](#atlfreemarshalstream)|Libère les données de Marshal et le `IStream` pointeur.|
|[AtlMarshalPtrInProc](#atlmarshalptrinproc)|Crée un objet de flux et marshale le pointeur d’interface spécifié.|
|[AtlUnmarshalPtr](#atlunmarshalptr)|Convertit les données de marshaling d’un flux en un pointeur d’interface.|

## <a name="requirements"></a>Conditions requises :

**En-tête :** atlbase. h

## <a name="atlfreemarshalstream"></a><a name="atlfreemarshalstream"></a> AtlFreeMarshalStream

Libère les données de marshaling dans le flux, puis libère le pointeur de flux.

```
HRESULT AtlFreeMarshalStream(IStream* pStream);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
dans Pointeur vers l' `IStream` interface sur le flux utilisé pour le marshaling.

### <a name="example"></a>Exemple

Consultez l’exemple pour [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="atlmarshalptrinproc"></a><a name="atlmarshalptrinproc"></a> AtlMarshalPtrInProc

Crée un objet de flux, écrit le CLSID du proxy dans le flux, puis marshale le pointeur d'interface spécifié en écrivant les données nécessaires pour initialiser le proxy dans le flux.

```
HRESULT AtlMarshalPtrInProc(
    IUnknown* pUnk,
    const IID& iid,
    IStream** ppStream);
```

### <a name="parameters"></a>Paramètres

*pUnk*<br/>
dans Pointeur vers l’interface à marshaler.

*vaut*<br/>
dans GUID de l’interface qui est marshalée.

*ppStream*<br/>
à Pointeur vers l' `IStream` interface sur le nouvel objet de flux utilisé pour le marshaling.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="remarks"></a>Notes

L’indicateur de MSHLFLAGS_TABLESTRONG est défini de sorte que le pointeur puisse être marshalé en plusieurs flux. Le pointeur peut également être démarshalé plusieurs fois.

Si le marshaling échoue, le pointeur de flux est libéré.

`AtlMarshalPtrInProc` peut uniquement être utilisé sur un pointeur vers un objet in-process.

### <a name="example"></a>Exemple

[!code-cpp[NVC_ATL_COM#50](../../atl/codesnippet/cpp/marshaling-global-functions_1.cpp)]

## <a name="atlunmarshalptr"></a><a name="atlunmarshalptr"></a> AtlUnmarshalPtr

Convertit les données de marshaling du flux en un pointeur d'interface qui peut être utilisé par le client.

```
HRESULT AtlUnmarshalPtr(
    IStream* pStream,
    const IID& iid,
    IUnknown** ppUnk);
```

### <a name="parameters"></a>Paramètres

*pStream*<br/>
dans Pointeur vers le flux qui est démarshalé.

*vaut*<br/>
dans GUID de l’interface qui est démarshalée.

*ppUnk*<br/>
à Pointeur vers l’interface démarshalée.

### <a name="return-value"></a>Valeur renvoyée

Valeur HRESULT standard.

### <a name="example"></a>Exemple

Consultez l’exemple pour [AtlMarshalPtrInProc](#atlmarshalptrinproc).

## <a name="see-also"></a>Voir aussi

[Fonctions](../../atl/reference/atl-functions.md)
